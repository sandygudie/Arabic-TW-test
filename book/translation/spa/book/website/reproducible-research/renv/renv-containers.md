(rr-renv-containers)=
# Containers

(rr-renv-containers-why)=
## Why Containers?

Even for moderately complex projects, the size of the software dependency stack can be huge. Take a simple pipeline to build a pdf report for an analysis scripted in R using `Rmarkdown`, for example. To make this reproducible, not only do (i) the respective R packages need to be installed and (ii) the R version needs to be the same, but also (iii) the versions of `pandoc` and `LaTeX` need to be the same as during runtime.

Instead of trying to resolve these dependencies via a package manager (such as conda) -  which also depends on all required software being available in a single package manager - it might be easier to create a snapshot of the entire computing environment including all dependencies. These computing environments are then self-contained, hence the name 'containers'.

(rr-renv-containers-what)=
## What are Containers?

Containers allow a researcher to package up a project with all of the parts it needs - such as libraries, dependencies, and system settings - and ship it all out as one package. Anyone can then open up a container and work within it, viewing and interacting with the project as if the machine they are accessing it from is identical to the machine specified in the container - regardless of what their computational environment _actually_ is. Están diseñados para facilitar la transferencia de proyectos entre entornos muy diferentes.

In a way, containers behave like a virtual machine. To the outside world, they look like their own complete system. However, unlike a virtual machine, rather than creating a whole virtual operating system plus all the software and tools typically packaged with one, containers only contain the individual components they need in order to operate the project they contain. This gives a significant performance boost and reduces the size of the application.

Containers are a particularly useful way for reproducing research which relies on software to be configured in a certain way, or which makes use of libraries that vary between (or do not exist on) different systems. In summary, containers are a more robust way of sharing reproducible research than package management systems or Binder because they reproduce the entire system used for the research, not just the packages explicitly used by it. Their major downside is that due to their greater depth, they are conceptually more difficult to grasp and produce than many other methods of replicating computational environments.

Ben Corrie give a reasonably accessible overview of core concepts in ['What is a container?'](https://www.youtube.com/watch?v=EnJ7qX9fkcU).

(rr-renv-containers-images)=
## What are Images?

Images are the files used to generate containers. Humans do not make images; they write recipes to generate images. Containers are then identical copies instantiated from images.

Think of it like this:

- A recipe file a human writes contains all the steps to generate a working version of the project and its computational environment, but no actual materials. Think of this as a blueprint.
- Building an image takes that recipe and using it, assembles all the packages, software libraries, and configurations needed to make the full-fledged project and environment, and bundles them up in a condensed lump. Think of images like a piece of flat-pack furniture made using the blueprint.
- Containers take that image and assemble a fully working version of the project and the environment needed to run it. Think of this as assembling the flat-pack furniture.

So if a researcher wants to allow others to reproduce their work, they would need to write a recipe file, and use it to build an image of their project. They can then share this image file with anyone who wants to replicate their work. That person can then use the image to generate a container containing a working version of the project.

(rr-renv-containers-docker)=
## What is Docker?

There are many tools available for creating and working with containers. We will focus on Docker, which is widely used, but be aware that others such as Singularity also exist. A veces se prefiere la singularidad para usar en sistemas de computación de alto rendimiento ya que no necesita `sudo` permisos para ejecutarse, mientras que Docker lo hace.

In Docker, the recipe files used to generate images are known as Dockerfiles, and should be named `Dockerfile`.

[Docker Hub](https://hub.docker.com/) alberga una gran cantidad de imágenes prediseñadas tales como [imágenes](https://hub.docker.com/_/ubuntu) de máquinas Ubuntu, que pueden ser descargadas y construidas. This makes the process of writing Dockerfiles relatively easy since users very rarely need to start from scratch, they can just customise existing images. However, this leaves a user vulnerable to similar security issues as described in the {ref}`rr-renv-yaml-security` of the {ref}`rr-renv-yaml` sub-chapter:

- It is possible to include malicious code in Docker images
- It is possible for people producing images to unknowingly include software in them with security vulnerabilities

[This](https://opensource.com/business/14/7/docker-security-selinux) article goes deeper into the potential security vulnerabilities of containers and here is a [detailed breakdown](https://opensource.com/business/14/9/security-for-docker) of security features currently within Docker, and how they function. The best advice for using images built by others is, as usual, only download and run something on your machine if it comes from a trusted source. Docker Hub has "official image" badges for commonly used, verified images as shown here:

```{figure} ../../figures/docker-official-image.png
---
name: docker-official-image
alt: A screenshot of official image badges
---
```

(rr-renv-containers-installdocker)=
## Installing Docker

Installers for Docker on a variety of different systems are available [here](https://docs.docker.com/install/). Detailed installation instructions are also available for a variety of operating systems such as [Ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu/), [Debian](https://docs.docker.com/install/linux/docker-ce/debian/), [Macs](https://docs.docker.com/docker-for-mac/install/), and [Windows](https://docs.docker.com/docker-for-windows/install/).

(rr-renv-containers-commands)=
## Key Commands

Here are a few key commands for creating and working with containers:

- To build an image from a Dockerfile, go to the directory where the Dockerfile is and run:
  ```
  sudo docker build --tag image_name .
  ```
- To list the images on your system, use:
  ```
  sudo docker image ls
  ```
- To remove an image, run:
  ```
  sudo docker rmi image_name
  ```
- To open a container from an image, run:
  ```
  sudo docker run -i -t image_name
  ```
  The `-i -t` flags automatically open up an interactive terminal within the container so you can view and interact with the project files.
- To exit an interactive terminal, use:
  ```
  exit
  ```
- To get a list of active containers with IDs, run:
  ```
  sudo docker container ls
  ```
- There are also three main commands used for changing the status of containers:
  - Pausing suspends the process running the container.
    ```
    sudo docker pause container_ID
    ```
    Containers can be unpaused by replacing `pause` with `unpause`.
  - Stopping a container terminates the process running it. A container must be stopped before it can be deleted.
    ```
    sudo docker stop container_ID
    ```
    A stopped container can be restarted by replacing `stop` with `restart`.
  - If `stop` does not work containers can be killed using
    ```
    sudo docker kill container_ID
    ```
- To remove a container, run:
  ```
  sudo docker rm container_ID
  ```
(rr-renv-containers-dockerfiles)=
## Writing Dockerfiles

Let us go through the anatomy of a very simple Dockerfile:

```
# Step 1: Set up the computational environment

# Set the base image
FROM ubuntu:18.04

# Install packages needed to run the project
RUN apt-get update && \
    apt-get install -y --no-install-recommends python3.7 python3-pip && \
    rm -rf /var/lib/apt/lists/*
RUN python3 -m pip install numpy

#-----------------------

# Step 2: Include the project files in the image

# Copy files from the `project_files` directory on the machine building the image
# into the `project` folder in the container. This folder and any missing
# directories in its path are created automatically.
COPY project_files/ project/
```

This looks complicated, but most of the lines in this example are comments (which are preceded by `#`'s). There are only six lines of actual code. The first of these is a `FROM` statement specifying a base image. All Dockerfiles require a FROM, even if it is just `FROM SCRATCH`. All the following commands in a Dockerfile build upon the base image to make a functioning version of the researcher's project. Specifying a version for the image (`18.04` in this case) is optional. However, it is best practice as it ensures that our Dockerfile remains valid after new releases of Ubuntu, which may not include packages (or specific versions thereof) that we require later (for example `python3.7`).

It is worth spending time to choose an appropriate base image, as doing so can reduce the amount of work involved in writing a Dockerfile dramatically. For example, a collection of images with the R programming language included in them can be found [here](https://github.com/rocker-org/rocker-versioned). If a project makes use of R, it is convenient to use one of these as a base image rather than spend time writing commands in your Dockerfile to install R.

The biggest block of lines comes next. It's a series of `RUN` statements, which run shell commands when building the image. In this block, they are used to install the software necessary to run the project. El primer bloque `RUN` es una cadena de comandos de este formulario:

```
RUN command_to_do_thing_1 \
   && command_to_do_thing_2 \
   && command_to_do_thing_3 \
   && command_to_do_thing_4
```

Es una buena práctica agrupar comandos relacionados en un solo bloque `RUN` para reducir el tamaño final de tu imagen en [evitando la creación de capas innecesarias](https://docs.docker.com/develop/develop-images/#minimize-the-number-of-layers). También seguimos la mejor práctica usando `--no-install-recommends` para [evitar la instalación de paquetes innecesarios](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/#dont-install-unnecessary-packages) y [limpiando el `apt-cache`](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/#run), ambas reducen aún más el tamaño de las imágenes de Debian o Ubuntu.

After we have installed Python, we use another RUN statement to install a library required by our code.

Finally the `COPY` command is used to copy the project files from the machine building the image into the image itself. The syntax of this command is `COPY file_to_copy location_in_container_to_copy_to`. In this example, all the files in the `project_files` directory are included in the `project` file in the container. Tenga en cuenta que sólo puede copiar archivos desde el directorio donde se encuentra Dockerfile, o subdirectorios dentro de él (en el ejemplo, que es el subdirectorio `project_files`).

The `ADD` command has the same capabilities as `COPY`, but it can also be used to add files not on the machine building the image. For example it can be used to include files hosted online by following `ADD` with a URL to the file. It is good practice to use `COPY`, except where `ADD` is specifically required, as the term `COPY` is more explicit about what is being done.

Here is what happens if a container is opened from an image called `book_example`, built from the example above:

```{figure} ../../figures/container-example.png
---
name: container-example
alt: A screenshot of what happens when a container is opened from an image
---
```

As you can see, the directory `project` has been created, and inside the project files, `analysis.py` and `data.csv` have been copied into it. Because the Dockerfile already includes the software required for the project, in the image, the `analysis.py` script runs without installing more software.

(rr-renv-containers-dockerfiles-workdir)=
### `WORKDIR`

This command can be used in Dockerfiles to change the current working directory. Commands that follow this in the Dockerfile will be applied within the new working directory unless/until another `WORKDIR` changes the working directory. When a container is opened with an interactive terminal, the terminal will open in the final working directory. Here is a simple example of a Dockerfile that uses `WORKDIR`, and the container it generates.

```
# Basic setup
FROM ubuntu
RUN apt-get update

# Make a directory called A
RUN mkdir A

# Make the working directory A
WORKDIR A

# Make two directories, one called B_1 and one called B_2
RUN mkdir B_1
RUN mkdir B_2
```

```{figure} ../../figures/workdir-example.png
---
name: workdir-example
alt: Screenshot of container generated using WORKDIR command
---
```

Directories `B_1` and `B_2` have been created within directory `A`.

`WORKDIR` should be used when changing directories is necessary while building an image. Puede ser tentador usar `RUN cd directory_name` en su lugar? ya que esta sintaxis será más familiar para aquellos que normalmente funcionan a través de la línea de comandos, pero esto puede llevar a errores. After each `RUN` statement in a Dockerfile, the image is saved, and any following commands are applied to the image anew. Como ejemplo, esto es lo que sucede en el ejemplo anterior si la línea `WORKDIR A` se intercambia por `RUN cd A`.

```{figure} ../../figures/cd-example.png
---
name: cd-example
alt: A screenshot of what happens when the WORKDIR command is swapped with RUN cd
---
```

All the directories have are in the top level in this case, rather than `B_1` and `B_2` being inside `A`. Esto se debe a que la imagen se reinició después del comando `RUN cd A` y se abrió en el nivel superior (root) por defecto, así que es donde los comandos `mkdir B_1` y `mkdir B_2` entraron en vigor.

(rr-renv-containers-dockerfiles-commands)=
### Other Commands

Other commands that are sometimes used in Dockerfiles include:

- `CMD`: This is used to run commands as soon as the container is opened. This is different to RUN commands which are commands run as part of _setting up_ a container. For example, to have a welcome message when a container is opened from the image, `CMD` could be used as follows:
  ```
  CMD ["echo","¡Bienvenido! ¡Acabas de abrir este contenedor!"] You just opened this container!"]
  ```
  Es una buena práctica usar CMD para cualquier comando que necesite ejecutarse antes de que alguien empiece a trabajar en el contenedor en lugar de forzar a los usuarios a ejecutarlos a sí mismos (y confiar en que incluso sabrán que necesitan).
- `VOLUMES`: These will be discussed {ref}`later <rr-renv-containers-volumes>`.
- `MAINTAINER`: This contains information regarding the person that wrote the Dockerfile. It is typically included at the top of a Dockerfile.
- `EXPOSE`: This includes ports that should be exposed. It is more relevant to people using Docker to share web apps.
- `USER`: Change the user that a command is run as (useful for dropping privileges).

(rr-renv-containers-dockerignore)=
## Building Images and `.dockerignore` Files

Como se menciona en la sección {ref}`comandos clave <rr-renv-containers-commands>` , para construir una imagen abra un terminal en el mismo directorio que el Dockerfile a ser usado y ejecutado:

```
sudo docker build --tag name_to_give_image .
```

When an image is built everything in the Dockerfile's directory and below (this is called the "context") is sent to the Docker daemon to build the image. The daemon uses the Dockerfile and its context to build the image. If the context contains many large files, which are not needed for building the image, (old datafiles, for example) then it is a waste of time sending them to the daemon. Doing so can make the process of building an image slow. Files can be excluded from the context by listing them in a text file called `.dockerignore`. It is good practice to do so.

The files do not need to be listed individually in the `.dockerignore` file. Here is an example of the contents of a `.dockerignore` file:

```
*.jpg
**/*.png
data_files/*
file_to_exclude.txt
```

This excludes from the context:

- All `.jpg` files in the same directory as the Dockerfile file
- All `.png` files in the same directory as the Dockerfile file _or any subdirectories within it_
- All files within the `data_files` directory
- The file named `file_to_exclude.txt`

(rr-renv-containers-sharing)=
## Sharing Images

Docker images can be shared most easily via [Docker Hub](https://hub.docker.com/), which requires an account. Say two researchers, Alice and Bob, are collaborating on a project and Alice wishes to share an image of some of her work with Bob.

To do this, Alice must:

- Write a Dockerfile to produce an image of her work.
- Build the image. She (being inventive) calls it image_name
- Go to DockerHub and sign up for an account. Say Alice (again, being inventive) chooses the username `username_Alice`
- Log into DockerHub via the terminal on her machine using:
  ```
  sudo docker login
  ```
- Tag the image of her project on her machine via the command line by supplying the name of the image and using the pattern `username/image_name:version`. So Alice runs the command:
  ```
  sudo docker tag image_name username_Alice/image_name:version_1
  ```
- Push the image to her Docker Hub account using:
  ```
  sudo docker tag push username_Alice/image_name:version_1
  ```
- Alice's image is now online and can be downloaded. Over to Bob...

Bob (assuming he already has Docker installed) can open a container from Alice's image simply by running

```
sudo docker run -i -t username_Alice/image_name:version_1
```

Initially, Docker will search for this image on Bob's machine. When it does not find it, it will _automatically_ search DockerHub, download Alice's image, and open the container with Alice's work and environment on Bob's machine.

(rr-renv-containers-copying)=
## Copying Files To And From Containers

Containers act much like virtual machines; as a result, copying files into and out of them is not as trivial as copying files to different locations within the same computer is.

A file can be copied from the machine running a container into the container using:

```
sudo docker cp file_name container_ID:path_to_where_to_put_file/file_name
```

Recall that container IDs can be obtained using `sudo docker container ls`.

A file can be copied from within a container to the machine running the container by running the following command on the machine running the container:

```
sudo docker cp container_ID:path_to_file/file_name path_to_where_to_put_file/file_name
```

If the second part (the `path_to_where_to_put_file/file_name`) is substituted for a `.`, then the file will be copied to whatever directory the terminal running the command is in.

(rr-renv-containers-volumes)=
## Volumes

Every time a container is opened from an image, that container is completely new. Say a container is opened, and work is done within it. If that container is closed, and the image it came from is again used to start another container, none of that work will be in the new one. It will simply have the starting state described in the image.

This can be a problem if a researcher wants to work in a container over time. Fortunately, there is a way around this using volumes. Volumes store the work done within a container even after it is closed, and can be used to load that work into future containers.

To create/use a volume, run:

```
sudo docker run -i -t --mount source=volume_name,target=/target_directory image_name
```

You should give your volume a more descriptive name than `volume_name`. A `target` directory is required; only work within this directory will be saved in the volume. Once the researcher is done, they can close the container as normal. When they come back to the project and want to continue their work, they only need to use the same command as above, and it will load the work contained in `volume_name` into the new container. It will save any new work there too.

Below is a list of volume related commands:

- To list volumes: `sudo docker volume ls`
- To delete a volume: `sudo docker volume rm volume_name`
- To delete all unattached volumes: `sudo docker volume prune`

If, when deleting a container, a `-v` is included after `rm` in `sudo docker rm container_ID`, any volumes associated with the container will also be deleted.

(rr-renv-contenedores-singularidad)=
## Singularidad

Up until April 2020, the only way to run Docker was with root access. "Rootless" mode was made available as part of the [v20.10](https://docs.docker.com/engine/security/rootless/) release. Rootless mode is currently only avaliable on Linux and requires an initial install of Docker >= v20.10.

The underyling difference between Docker without and with rootless mode is that perviously any system running Docker had a daemon running as `uid0` that creates and owns all images, but with rootless mode the user creates and owns any images that they initialize. To install and run the rootless version of Docker as a non-root user, use the following commands (where `20.10` refers to the installed version of Docker):

```
concha de singularidad docker://ubuntu
```

The following prequisites, which are part of the [`shadow-utils`](https://github.com/shadow-maint/shadow) package are required to run Docker rootless: `newuidmap` and `newgidmap`.

(rr-renv-containers-singularity)=
## Palabras de Advertencia


> **Prerequisites**: At present, Singularity only runs on Linux systems (for example Ubuntu). If you use macOS, [Singularity Desktop for macOS](https://www.sylabs.io/singularity-desktop-macos/) is in "Beta" release stage.

Un inconveniente significativo de usar Docker para investigaciones reproducibles es que no está pensado como una aplicación de espacio de usuario sino como una herramienta para administradores de servidores. Como tal, requiere acceso root para funcionar. Sin embargo, no hay ninguna razón por la que la ejecución de un análisis deba requerir acceso root para el usuario. Esto es especialmente importante cuando los cálculos se llevan a cabo en un recurso compartido como los sistemas HPC donde los usuarios nunca tendrán acceso root.

Se introdujo el software contenedor de [singularidad](https://www.sylabs.io/) para abordar este problema. La singularidad se creó con sistemas HPC y la investigación reproducible en mente (ver \[this\](https://www.youtube.com/watch?v=DA87Ba2dpNM video). No requiere acceso root para ejecutarse (¡sólo para construir _imágenes del contenedor_! , y por lo tanto permite a los usuarios de HPC construir imágenes de contenedores localmente antes de ejecutar análisis en un clúster de alto rendimiento, por ejemplo. Como beneficio añadido, esto hace posible el uso de casi cualquier software en un sistema HPC sin tener que molestar al personal de administración con la instalación.

Además, dado que Docker es _el_ enfoque de contenedor más conocido, la singularidad apunta a mantener la compatibilidad con contenedores docker. Esto significa que la singularidad puede ser usada para ejecutar contenedores docker normales (sin requerir acceso root).

La singularidad puede utilizarse para ejecutar imágenes Docker o ampliarlas construyendo nuevas imágenes basadas en contenedores docker como una capa base. Por ejemplo, podríamos usar singularidad para crear un contenedor de vainilla ubuntu con una shell usando la imagen de docker de ubuntu:

```
Bootstrap: docker
De: ubuntu

%post
    apt-get -y update
    apt-get -y install fortune cowsay lolcat

%environment
    export LC_ALL=C
    export PATH=/usr/games:$PATH

%runscript
    fortune | cowsay | lolcat
```

> (type `exit` to leave the interactive shell again).

Así como las imágenes docker se construyen utilizando archivos `Dockerfile` , los contenedores de singularidad se construyen a partir de archivos de definición de singularidad. El proceso y la sintaxis son similares a los archivos docker, pero hay diferencias sutiles. Como un ejemplo de trabajo mínimo, podemos construir un contenedor de `lolcow` basado en la imagen oficial del contenedor docker ubuntu. Pon lo siguiente en un archivo `lolcow.def` (basado en la [documentación de Singularidad](https://www.sylabs.io/guides/3.2/user-guide/build_a_container.html)):
```
Bootstrap: docker
From: ubuntu

%post
    apt-get -y update
    apt-get -y install fortune cowsay lolcat

%environment
    export LC_ALL=C
    export PATH=/usr/games:$PATH

%runscript
    fortune | cowsay | lolcat
```

Esta 'receta' utiliza una imagen docker como base (`ubuntu`), instala algunos paquetes `apt` , modifica algunas variables de entorno, y especifica el script de ejecución `` (que se ejecuta usando el comando `de ejecución` de singularidad). Los detalles sobre el formato de archivo de definición de singularidad se pueden encontrar en la documentación oficial [](https://www.sylabs.io/docs/).

(rr-renv-containers-singularidad-almacenamiento)=

```
sudo singularity build lolcow.simg lolcow.def
```

Esto extraerá la imagen ubuntu de DockerHub, ejecuta los pasos de la receta en el archivo de definición y produce un único archivo de imagen de salida (`lolcow. img`). Finalmente se ejecuta el `runscript` como

```
singularidad correr lolcow.simg
```

Idealmente, debería ver una buena vaca ASCII y unas pocas palabras de sabiduría:

```
___________________________________
/ Serás llamado para ayudar a un \
\ amigo en problemas.                /
-----------------------------------
       \   ^__^
        \  (oo)\_______
           (__)\       )\/\
               ||----w |
               ||     ||
```

Siendo compatible con HPC, los contenedores de singularidad también están soportados por una amplia gama de herramientas de gestión de flujo de trabajo. Por ejemplo, tanto [snakemake](https://snakemake.readthedocs.io/en/stable/) como [nextflow](https://www.nextflow.io/docs/latest/singularity.html) soportan contenedores de singularidad específicos para el trabajo. Esto hace que los contenedores de singularidad sean únicos para paralelizar los flujos de trabajo en sistemas HPC utilizando el extensamente utilizado gestor de carga de trabajo de [slurm](https://slurm.schedmd.com/documentation.html). Utilizando singularidad, contenedores y snakemake/nextflow es una manera de escalar la reproducibilidad a una escala masiva. Además, como beneficio añadido, traer flujos de trabajo desde una máquina de escritorio a un sistema HPC ya no requiere escribir scripts de trabajo personalizados.

(rr-renv-containers-singularity-storage)=
### Long-term Storage of Container Images

Es importante tener en cuenta que un simple archivo de receta de contenedor no es reproducible en sí mismo, ya que el proceso de compilación depende de varias fuentes (en línea). Por lo tanto, el mismo archivo de receta podría llevar a diferentes imágenes si se actualizaran las fuentes subyacentes.

Para lograr una verdadera reproducibilidad, es importante almacenar las _imágenes_ del contenedor real. Para las imágenes de singularidad, esto es particularmente fácil, ya que una imagen es simplemente un archivo grande. Pueden variar en tamaño, desde unas pocas decenas de megabytes (microcontenedores) hasta varios gigabytes, y por lo tanto no son adecuados para ser almacenados en un repositorio git ellos mismos Un libre, citable, y solución a largo plazo para almacenar imágenes de contenedores es [zenodo. rg](https://zenodo.org/) que permite hasta 50 Gb por repositorio. Dado que zenodo mints DOI para todo el contenido cargado, las imágenes son inmediatamente citables. En contraste con [Docker Hub](https://hub.docker.com/) (que también acepta solo imágenes docker), zenodo también está claramente engrandecido hacia el almacenamiento y la detección a largo plazo mediante un sofisticado sistema de metadatas. Por lo tanto, es ideal para almacenar contenedores científicos asociados con análisis particulares, ya que estos tienden a no cambiar con el tiempo.

(rr-renv-containers-warning)=
## Words of Warning

Aunque la singularidad y el estibador pueden parecer similares, son conceptualmente muy diferentes. Además del hecho obvio de que la singularidad no requiere acceso root para ejecutar contenedores, también maneja la distinción entre el sistema de ficheros anfitrión y contenedor de forma diferente. Por ejemplo, por defecto, la singularidad incluye algunos puntos de enlace en el contenedor, a saber:

- `$HOME`
- `/sys:/sys`
- `/proc:/proc`
- `/tmp:/tmp`
- `/var/tmp:/var/tmp`
- `/etc/resolv.conf:/etc/resolv.conf`
- `/etc/passwd:/etc/passwd`
- `$PWD`

Nota, `$PWD` es práctico ya que implica que todos los archivos en el directorio de trabajo son visibles dentro del contenedor. Enlazando `$HOME` por defecto, sin embargo, también implica que el software que utiliza archivos de configuración de `$HOME` podría comportarse de forma inesperada ya que los archivos de configuración específicos de la imagen se sobrescriben con la configuración actual de los usuarios en `$HOME`. Aunque este comportamiento es práctico en escenarios HPC, es potencialmente peligroso para la investigación reproducible. Para evitar posibles problemas, cualquier software instalado en un contenedor de singularidad debería estar apuntado a un archivo de configuración global independiente del usuario.
