(rr-renv-containers)=
# Containers

(rr-renv-containers-why)=
## Why Containers?

Even for moderately complex projects, the size of the software dependency stack can be huge. Take a simple pipeline to build a pdf report for an analysis scripted in R using `Rmarkdown`, for example. لجعل هذا قابل للتأثر، لا يقتصر الأمر على ما يلي: `1` ضرورة تركيب حزم إعادة التدوير ذات الصلة، و`2` ضرورة أن تكون صيغة إعادة التدوير هي نفسها، ولكن أيضا '3`إصدارات`Pandoc`و`LaTeX` يجب أن تكون نفس الإصدارات أثناء التشغيل.

Instead of trying to resolve these dependencies via a package manager (such as conda) -  which also depends on all required software being available in a single package manager - it might be easier to create a snapshot of the entire computing environment including all dependencies. These computing environments are then self-contained, hence the name 'containers'.

(rr-renv-containers-what)=
## What are Containers?

Containers allow a researcher to package up a project with all of the parts it needs - such as libraries, dependencies, and system settings - and ship it all out as one package. Anyone can then open up a container and work within it, viewing and interacting with the project as if the machine they are accessing it from is identical to the machine specified in the container - regardless of what their computational environment _actually_ is. تم تصميمها لجعلها أسهل نقل المشاريع بين بيئات مختلفة جدا.

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

There are many tools available for creating and working with containers. We will focus on Docker, which is widely used, but be aware that others such as Singularity also exist. يفضل التفرد في بعض الأحيان لاستخدامه في نظم الحوسبة عالية الأداء لأنه لا يحتاج إلى أذونات `sudo` ليتم تشغيلها، في حين يفعل Docker.

In Docker, the recipe files used to generate images are known as Dockerfiles, and should be named `Dockerfile`.

[Docker Hub](https://hub.docker.com/) يستضيف العديد من الصور المصنوعة مسبقاً، مثل [صور](https://hub.docker.com/_/ubuntu) لماكينات أوبونتو، التي يمكن تنزيلها والبناء عليها. This makes the process of writing Dockerfiles relatively easy since users very rarely need to start from scratch, they can just customise existing images. However, this leaves a user vulnerable to similar security issues as described in the {ref}`rr-renv-yaml-security` of the {ref}`rr-renv-yaml` sub-chapter:

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

The biggest block of lines comes next. It's a series of `RUN` statements, which run shell commands when building the image. In this block, they are used to install the software necessary to run the project. كتلة `RUN` الأولى هي سلسلة أوامر من هذا النموذج:

```
RUN command_to_do_thing_1 \
   && command_to_do_thing_2 \
   && command_to_do_thing_3 \
   && command_to_do_thing_4
```

من الممارسات الجيدة تجميع الأوامر ذات الصلة في كتلة واحدة `RUN` لتقليل الحجم النهائي لصورك ب [لتجنب إنشاء طبقات غير ضرورية](https://docs.docker.com/develop/develop-images/#minimize-the-number-of-layers). نحن أيضا نتابع أفضل الممارسات باستخدام `--no-install-recommend` إلى [لتجنب تثبيت حزم غير ضرورية](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/#dont-install-unnecessary-packages) و [لتنظيف ذاكرة التخزين المؤقت ``](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/#run)، وكلاهما يقلل من حجم صور ديبا أو أوبونتو.

After we have installed Python, we use another RUN statement to install a library required by our code.

Finally the `COPY` command is used to copy the project files from the machine building the image into the image itself. The syntax of this command is `COPY file_to_copy location_in_container_to_copy_to`. في هذا المثال ، يتم تضمين جميع الملفات في دليل `project_files` في ملف المشروع `` في الحاوية. لاحظ أنه يمكنك فقط نسخ الملفات من الدليل حيث يوجد ملف Docker، أو الدلائل الفرعية داخلها (في المثال ، هذا هو `project_files` subdirectory).

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

`WORKDIR` should be used when changing directories is necessary while building an image. قد يكون من المغري استخدام `RUN cd directory_name` بدلاً من ذلك، لأن هذه الجملة ستكون أكثر إلماماً بتلك التي تعمل عادة عبر سطر الأوامر، ولكن هذا يمكن أن يؤدي إلى أخطاء. After each `RUN` statement in a Dockerfile, the image is saved, and any following commands are applied to the image anew. على سبيل المثال، هنا ما يحدث في المثال أعلاه إذا تم تبديل سطر `WORKDIR A` مقابل `RUN cd A`.

```{figure} ../../figures/cd-example.png
---
name: cd-example
alt: A screenshot of what happens when the WORKDIR command is swapped with RUN cd
---
```

All the directories have are in the top level in this case, rather than `B_1` and `B_2` being inside `A`. هذا لأن الصورة تمت إعادة تشغيلها بعد أمر `RUN cd A` وفتحها في أعلى مستوى (الجذر) بشكل افتراضي، بحيث يكون هذا هو المكان الذي بدأ فيه نفاذ الأوامر `mkdir B_1` و `mkdir B_2`.

(rr-renv-containers-dockerfiles-commands)=
### Other Commands

Other commands that are sometimes used in Dockerfiles include:

- `CMD`: This is used to run commands as soon as the container is opened. This is different to RUN commands which are commands run as part of _setting up_ a container. For example, to have a welcome message when a container is opened from the image, `CMD` could be used as follows:
  ```
  CMD ["echo","Welcome! You just opened this container!"]
  ```
  من الممارسات الجيدة استخدام CMD لأي أوامر تحتاج إلى تشغيلها قبل أن يبدأ شخص العمل في الحاوية بدلا من إجبار المستخدمين على تشغيلها بأنفسهم (والثقة بأنهم سيعلمون حتى أنهم بحاجة إليهم).
- `VOLUMES`: These will be discussed {ref}`later <rr-renv-containers-volumes>`.
- `MAINTAINER`: This contains information regarding the person that wrote the Dockerfile. It is typically included at the top of a Dockerfile.
- `EXPOSE`: This includes ports that should be exposed. It is more relevant to people using Docker to share web apps.
- `USER`: Change the user that a command is run as (useful for dropping privileges).

(rr-renv-containers-dockerignore)=
## Building Images and `.dockerignore` Files

كما ذكر في {ref}`أوامر المفاتيح <rr-renv-containers-commands>` القسم ، لبناء صورة فتح محطة طرفية في نفس الدليل كـ ملف Dockerfile الذي سيتم استخدامه وتشغيله:

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

(rr-renv-containers-singarity)=
## التفرد

Up until April 2020, the only way to run Docker was with root access. "Rootless" mode was made available as part of the [v20.10](https://docs.docker.com/engine/security/rootless/) release. Rootless mode is currently only avaliable on Linux and requires an initial install of Docker >= v20.10.

The underyling difference between Docker without and with rootless mode is that perviously any system running Docker had a daemon running as `uid0` that creates and owns all images, but with rootless mode the user creates and owns any images that they initialize. To install and run the rootless version of Docker as a non-root user, use the following commands (where `20.10` refers to the installed version of Docker):

```
قذيفة مفردة docker://ubuntu
```

The following prequisites, which are part of the [`shadow-utils`](https://github.com/shadow-maint/shadow) package are required to run Docker rootless: `newuidmap` and `newgidmap`.

(rr-renv-buers-warning)=
## كلمات التحذير


> **Prerequisites**: At present, Singularity only runs on Linux systems (for example Ubuntu). If you use macOS, [Singularity Desktop for macOS](https://www.sylabs.io/singularity-desktop-macos/) is in "Beta" release stage.

ومن العيوب الهامة لاستخدام Docker في البحوث القابلة للتكرار، أنه لا يقصد به أن يكون تطبيقا للفضاء بين المستخدمين، بل أن يكون أداة لمديري الخوادم. ومن هذا المنطلق، يتطلب الوصول الجذري إلى العمل. غير أنه لا يوجد سبب يدعو إلى أن يتطلب إجراء تحليل إمكانية وصول المستعملين إلى جذورها. وهذا مهم بشكل خاص عندما تجري الحسابات على مورد مشترك مثل نظم HPC حيث لن يكون للمستخدمين أي إمكانية للوصول إلى الجذر.

تم تقديم برنامج حاوية [وحدة](https://www.sylabs.io/) لمعالجة هذه المشكلة. تم إنشاء وحدة مع أنظمة HPC والبحوث القابلة لإعادة التدوين في الاعتبار (انظر \[this\](https://www.youtube.com/watch?v=DA87Ba2dpNM فيديو). لا يتطلب الوصول إلى الجذر لتشغيله (فقط لبناء حاوية _صور_! ومن ثم يمكن مستخدمي الحواسيب HPC من بناء صور للحاويات محليا قبل إجراء تحليلات لمجموعة عالية الأداء، على سبيل المثال. وكمنفعة إضافية، وهذا يجعل من الممكن استخدام أي برنامج حاسوبي تقريبا على نظام HPC دون الحاجة إلى إثراء الموظفين الإداريين بتثبيته.

علاوة على ذلك، بما أن Docker هو __ نهج النقل بالحاويات الأكثر شهرة، فإن التفرد يهدف إلى الحفاظ على التوافق مع حاويات الرصيف. هذا يعني أنه يمكن استخدام الوحدة لتشغيل حاويات الأرصفة العادية (دون الحاجة إلى الوصول إلى الجذر!).

يمكن استخدام التفرد لتشغيل صور Docker أو توسيعها عن طريق بناء صور جديدة مبنية على حاويات الأرصفة كطبقة قاعدة. على سبيل المثال، يمكننا استخدام التفرد لإنشاء حاوية فانيليا أوبونتو مع قذيفة باستخدام صورة رصيف أوبونتو:

```
Bootstrap: docker
من: ubuntu

%post
    apt-get -y تحديث
    apt-get - y install ثروة البقر

%en<unk> ment
    تصدير LC_ALL=C
    تصدير PATH=/usr/games:$PATH

%runscript
    fortune <unk> cowsay <unk> lolcat
```

> (type `exit` to leave the interactive shell again).

تماما كما يتم بناء صور المرفأ باستخدام ملفات `Dockerfile` ، يتم بناء حاويات التفرد من ملفات تعريف الوحدة. العملية و الجملة مشابهة لملف المرفأ، ولكن هناك اختلافات دقيقة. كحد أدنى من الأمثلة على العمل، يمكننا بناء حاوية `Lolcow` استنادًا إلى صورة حاوية حاوية أوبونتو الرسمية. ضع ما يلي في ملف `lolcow.def` (استناداً إلى [مستندات التفرد](https://www.sylabs.io/guides/3.2/user-guide/build_a_container.html):
```
قم ببناء الوحدة lolcow.simg lolcow.def
```

هذه 'الوصفة' تستخدم صورة دفتر كأساس (`ubuntu`)، تثبيت بعض `حزم apt` ، وتعديل بعض متغيرات البيئة ، ويحدد البرنامج النصي `` (الذي يتم تنفيذه باستخدام `تشغيل الوحدة` الأمر). يمكن العثور على تفاصيل تنسيق ملف تعريف التفرد في [الوثائق الرسمية](https://www.sylabs.io/docs/).

(rr-renv-containers-singarity-storage)=

```
وحدة تشغيل lolcow.simg
```

سيؤدي هذا إلى سحب صورة أوبونتو من دوكيرهوب، قم بتشغيل خطوات الوصفة في ملف التعريف وانتاج ملف صورة مخرج واحد (`Lolcow. img`). أخيرا تم تنفيذ `runscript` كـ

```
singularity run lolcow.simg
```

من الناحية المثالية، يجب أن ترى بقرة لطيفة من طراز ASCII وبعض كلمات الحكمة:

```
___________________________________
/ سيتم دعوتك لمساعدة \
\ صديق في مشكلة.                /
-----------------------------------
       \   ^__^
        \  (oo)\_______
           (__)\       )\/\
               ||----w |
               ||     ||
```

وبما أن الحاويات تتمشى مع HPC، فإن الحاويات الفريدة مدعومة أيضا بطائفة واسعة من أدوات إدارة سير العمل. على سبيل المثال، يدعم كل من [snakemake](https://snakemake.readthedocs.io/en/stable/) و [nextflow](https://www.nextflow.io/docs/latest/singularity.html) حاويات أحادية لوظيفة محددة. وهذا يجعل الحاويات الفريدة مناسبة بشكل فريد لتوازي تدفق العمل في نظم HPC باستخدام مدير عبء العمل في [الفقير](https://slurm.schedmd.com/documentation.html) المستخدم على نطاق واسع. فاستخدام التفرد والحاويات والتدفق اللاحق هو طريقة لتوسيع نطاق إمكانية التكرار إلى نطاق هائل. وعلاوة على ذلك، وكفائدة إضافية، لم يعد جلب تدفقات العمل من آلة حاسوبية مكتبية إلى نظام HPC يتطلب كتابة نصوص مخصصة لتقديم الوظائف.

(rr-renv-containers-singularity-storage)=
### Long-term Storage of Container Images

ومن المهم الإشارة إلى أن مجرد ملف وصفة الحاويات لا يمكن تكراره في حد ذاته لأن عملية البناء تعتمد على مصادر مختلفة (متاحة على الإنترنت). ومن ثم فإن نفس ملف الوصفة قد يؤدي إلى صور مختلفة إذا تم تحديث المصادر الأساسية.

لتحقيق إمكانية التكرار الحقيقية، من المهم تخزين الحاوية الفعلية _صور_. بالنسبة لصور التفرد، هذا أمر سهل بشكل خاص لأن الصورة هي ببساطة ملف كبير. ويمكن أن تختلف هذه الأشكال من حيث الحجم، من بضع عشرات من الحاويات الدقيقة إلى عدة غيغابايت، وبالتالي فهي غير مناسبة لتخزينها في مستودع git نفسه مجاناً، والحل الطويل الأجل لتخزين صور الحاويات هو [زينودو. rg](https://zenodo.org/) الذي يسمح بما يصل إلى 50 جيغابايت لكل مستودع. بما أن تعدين zenodo DOIs لجميع المحتويات التي تم تحميلها، فإن الصور يمكن الاستشهاد بها على الفور. Since zenodo mints DOIs for all content uploaded, the images are immediately citable. In contrast to [Docker Hub](https://hub.docker.com/) (which also only accepts docker images), zenodo is also clearly geared towards long-term storage and discoverability via a sophisticated metadata system. ومن ثم فهو مناسب بشكل مثالي لتخزين الحاويات العلمية المرتبطة بتحليلات معينة لأن هذه الحاويات لا تتغير بمرور الوقت.

(rr-renv-containers-warning)=
## Words of Warning

وعلى الرغم من أن التفرد والمركبة قد تبدو متماثلة، فإنهما مختلفان جدا من الناحية المفاهيمية. وإلى جانب الحقيقة الواضحة المتمثلة في أن التفرد لا يتطلب الوصول الجذري إلى الحاويات المشغّلة، كما أنه يعالج التمييز بين نظام ملفات الحاويات والمضيف بطريقة مختلفة. على سبيل المثال، بشكل افتراضي، تتضمن الوحدة بضع نقاط ربط في الحاوية، وهي:

- `$HOME`
- `/sys:/sys`
- `/proc:/proc`
- `/tmp:/tmp`
- `/var/tmp:/var/tmp`
- `/etc/resolv.conf:/etc/resolv.conf`
- `/etc/passwd:/etc/passwd`
- `$PWD`

ملاحظة: `$PWD` يأتي في متناول اليد، لأنه يعني أن جميع الملفات في دليل العمل مرئية داخل الحاوية. غير أن ربط `$HOME` بشكل افتراضي يعني أيضا أن البرنامج باستخدام ملفات التكوين من `$HOME` قد يتصرف بشكل غير متوقع لأن ملفات التكوين الخاصة بالصورة قد تم الكتابة فوقها مع إعدادات المستخدمين الحاليين في `$HOME`. وفي حين أن هذا السلوك مفيد في سيناريوهات مركبات الكربون الهيدروكلورية فلورية، فإنه يحتمل أن يكون خطراً على البحوث القابلة للتكرار. وتفاديا للمشاكل المحتملة، ينبغي الإشارة إلى أي برنامج حاسوبي مركب في حاوية مفردة إلى ملف تشكيل عالمي مستقل للمستعملين.
