(rr-renv-containers)=
# Containers

(rr-renv-containers-why)=
## Why Containers?

Even for moderately complex projects, the size of the software dependency stack can be huge. Take a simple pipeline to build a pdf report for an analysis scripted in R using `Rmarkdown`, for example. To make this reproducible, not only do (i) the respective R packages need to be installed and (ii) the R version needs to be the same, but also (iii) the versions of `pandoc` and `LaTeX` need to be the same as during runtime.

Instead of trying to resolve these dependencies via a package manager (such as conda) -  which also depends on all required software being available in a single package manager - it might be easier to create a snapshot of the entire computing environment including all dependencies. These computing environments are then self-contained, hence the name 'containers'.

(rr-renv-containers-what)=
## What are Containers?

Containers allow a researcher to package up a project with all of the parts it needs - such as libraries, dependencies, and system settings - and ship it all out as one package. 然后任何人都可以打开容器并在容器内工作。 查看并与项目交互，好像他们从容器中访问的机器与容器中指定的机器是相同的。 不管他们的计算环境 _实际是_ 是什么。 它们的设计是为了使 更容易在非常不同的环境之间传输项目。

In a way, containers behave like a virtual machine. To the outside world, they look like their own complete system. However, unlike a virtual machine, rather than creating a whole virtual operating system plus all the software and tools typically packaged with one, containers only contain the individual components they need in order to operate the project they contain. This gives a significant performance boost and reduces the size of the application.

Containers are a particularly useful way for reproducing research which relies on software to be configured in a certain way, or which makes use of libraries that vary between (or do not exist on) different systems. 概括而言， 容器是一种比包件管理系统或Binder更强有力的分享可再生产研究的方法，因为它们复制了用于研究的整个系统。 它们在概念上比许多其他重复计算环境的方法更难掌握和生产。

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

There are many tools available for creating and working with containers. We will focus on Docker, which is widely used, but be aware that others such as Singularity also exist. 高性能计算系统有时更喜欢使用独特性，因为它不需要 `sudo` 权限来运行，而停靠机器。

In Docker, the recipe files used to generate images are known as Dockerfiles, and should be named `Dockerfile`.

[Docker Hub](https://hub.docker.com/) 有许多事先制作的图片， 例如： [图像](https://hub.docker.com/_/ubuntu) Ubuntu 机器，可以下载和扩展。 This makes the process of writing Dockerfiles relatively easy since users very rarely need to start from scratch, they can just customise existing images. However, this leaves a user vulnerable to similar security issues as described in the {ref}`rr-renv-yaml-security` of the {ref}`rr-renv-yaml` sub-chapter:

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

This looks complicated, but most of the lines in this example are comments (which are preceded by `#`'s). There are only six lines of actual code. The first of these is a `FROM` statement specifying a base image. All Dockerfiles require a FROM, even if it is just `FROM SCRATCH`. All the following commands in a Dockerfile build upon the base image to make a functioning version of the researcher's project. Specifying a version for the image (`18.04` in this case) is optional. 然而，这是最佳做法，因为它确保我们的 Dockerfile 在新版本的 Ubuntu 之后仍然有效， 它可能不包括我们稍后需要的软件包 (或其中的特定版本) (例如， `python3)。 `。

It is worth spending time to choose an appropriate base image, as doing so can reduce the amount of work involved in writing a Dockerfile dramatically. For example, a collection of images with the R programming language included in them can be found [here](https://github.com/rocker-org/rocker-versioned). If a project makes use of R, it is convenient to use one of these as a base image rather than spend time writing commands in your Dockerfile to install R.

The biggest block of lines comes next. It's a series of `RUN` statements, which run shell commands when building the image. In this block, they are used to install the software necessary to run the project. 第一个 `RUN` 块是这种形式的 命令链：

```
RUN command_to_do_thing_1 \
   && command_to_do_thing_2 \
   && command_to_do_thing_3 \
   && command_to_do_thing_4
```

It is good practice to group related commands into a single `RUN` block to reduce the final size of your image by [avoiding the creation of unnecessary layers](https://docs.docker.com/develop/develop-images/#minimize-the-number-of-layers). We also follow best-practice by using `--no-install-recommends` to [avoid installing unnecessary packages](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/#dont-install-unnecessary-packages) and [cleaning up the `apt-cache`](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/#run), both of which further reduce the size of Debian or Ubuntu images.

After we have installed Python, we use another RUN statement to install a library required by our code.

Finally the `COPY` command is used to copy the project files from the machine building the image into the image itself. The syntax of this command is `COPY file_to_copy location_in_container_to_copy_to`. In this example, all the files in the `project_files` directory are included in the `project` file in the container. 注意您只能从 Dockerfile 所在目录复制文件， 或它内的子目录(例如为 `project_files` 子目录)。

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

This command can be used in Dockerfiles to change the current working directory. Commands that follow this in the Dockerfile will be applied within the new working directory unless/until another `WORKDIR` changes the working directory. When a container is opened with an interactive terminal, the terminal will open in the final working directory. 当一个容器与一个交互式终端打开时，终端将在最后工作目录中打开. 这是一个使用 `WORKDIR`和它生成的容器的 Dockerfile的简单例子。

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

`WORKDIR` should be used when changing directories is necessary while building an image. 它可能诱惑使用 `RUN cd directory_name` 因为这个语法对于那些通常通过命令行工作的人来说更加熟悉。 但这可能导致错误。 After each `RUN` statement in a Dockerfile, the image is saved, and any following commands are applied to the image anew. As an example, here is what happens in the above example if the `WORKDIR A` line is swapped for `RUN cd A`.

```{figure} ../../figures/cd-example.png
---
name: cd-example
alt: A screenshot of what happens when the WORKDIR command is swapped with RUN cd
---
```

All the directories have are in the top level in this case, rather than `B_1` and `B_2` being inside `A`. 这是因为图像在 `RUN cd A` 命令后重新启动，并默认在顶级(root) 级别打开， 所以 `mkdir B_1` 和 `mkdir B_2` 命令生效的地方。

(rr-renv-containers-dockerfiles-commands)=
### Other Commands

Other commands that are sometimes used in Dockerfiles include:

- `CMD`: This is used to run commands as soon as the container is opened. This is different to RUN commands which are commands run as part of _setting up_ a container. For example, to have a welcome message when a container is opened from the image, `CMD` could be used as follows:
  ```
  CMD ["回声","欢迎! 你刚刚打开了这个容器！"] You just opened this container!"]
  ```
  在某人开始在容器 工作之前需要运行的任何命令都使用CMD，而不是强迫用户自己运行它们（而且相信他们甚至知道自己需要）是很好的做法。
- `VOLUMES`: 这些将会在稍后讨论 {ref}`<rr-renv-containers-volumes>`
- `MAINTAINER`: This contains information regarding the person that wrote the Dockerfile. It is typically included at the top of a Dockerfile.
- `EXPOSE`: This includes ports that should be exposed. It is more relevant to people using Docker to share web apps.
- `USER`: Change the user that a command is run as (useful for dropping privileges).

(rr-renv-containers-dockerignore)=
## Building Images and `.dockerignore` Files

将相关命令分组为单个 `RUN` 块是一个好的做法，以减少您图像的最终大小为 [避免创建不必要的图层](https://docs.docker.com/develop/develop-images/#minimize-the-number-of-layers) 我们还遵循最佳做法，使用 `--no-install-recommended` to [避免安装不必要的软件包](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/#dont-install-unnecessary-packages) 和 [清理 `apt-cache`](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/#run)两者都进一步缩小了Debian 或 Ubuntu 图像的大小。

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

如果第二部分 ( `path_to_where_to_put_file/file_name`) 被替换为 ``然后文件将被复制到运行命令的终端目录中。

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

(rr-renv-containers-sinularity)=
## 独一无二性

Up until April 2020, the only way to run Docker was with root access. "Rootless" mode was made available as part of the [v20.10](https://docs.docker.com/engine/security/rootless/) release. Rootless mode is currently only avaliable on Linux and requires an initial install of Docker >= v20.10.

The underyling difference between Docker without and with rootless mode is that perviously any system running Docker had a daemon running as `uid0` that creates and owns all images, but with rootless mode the user creates and owns any images that they initialize. To install and run the rootless version of Docker as a non-root user, use the following commands (where `20.10` refers to the installed version of Docker):

```
单纯的 shell docker://ubuntu
```

Furthermore, since Docker is _the_ most well-known containerization approach, singularity aims at maintaining compatibility with docker containers. 这意味着单一性可以用来运行正常的停泊器容器(不需要root存取!)。

(rr-renv-containers-singularity)=
## 警告单词


> **前提条件**: 目前单纯性只在 Linux 系统上运行 (例如，Ubuntu). 如果您使用 macOS， [macOS 的 Singularity 桌面](https://www.sylabs.io/singularity-desktop-macos/) 处于“Beta”发布阶段。 If you use macOS, [Singularity Desktop for macOS](https://www.sylabs.io/singularity-desktop-macos/) is in "Beta" release stage.

使用 Docker进行可复制研究的一个重要缺陷是，它不是作为一个用户空间应用，而是作为服务器管理员的工具。 因此，它需要有根基才能运作。 然而，没有理由为什么进行分析需要用户获得Root权限。 当使用用户永远不会有Root权限的高清系统等共享资源进行计算时，这一点尤其重要。

为了解决这个问题，引入了 [独一无二的](https://www.sylabs.io/) 集装箱软件。 高频谱系统创建了独特性并考虑到可复制的研究(见 \[this\](https://www.youtube.com/watch?v=DA87Ba2dpNM video)。 它不需要运行 root 权限(仅构建容器 _镜像_！ 这样，HPC用户就能在当地制作容器图像，然后才能对高性能集群进行分析。 As an added benefit, this makes it possible to use almost any software on an HPC system without having to bother admin staff with installing it.

Furthermore, since Docker is _the_ most well-known containerization approach, singularity aims at maintaining compatibility with docker containers. This means that singularity can be used to run normal docker containers (without requiring root access!).

独特性可以用来运行 Docker 图像或通过基于基层的 docker 容器构建新图像来扩展它们。 例如，我们可以使用单独的方式创建一个带有炮弹的原生的ubuntu容器，使用 ubuntu 码头图像：

```
Bootstrap: docker
From: ubuntu

%post
    apt-get -y update
    apt-get -y install friche cowsay lolcat

%enintranment
    export LC_ALL=C
    export PATH=/usr/games:$PATH

%runscript
    frife | cowsay | lolcat
```

> (type `exit` to leave the interactive shell again).

Just as docker images are built using `Dockerfile` files, singularity containers are built from singularity definition files. 进程和语法类似于码头文件，但有微妙的差异。 The process and syntax are similar to docker files, but there are subtle differences. 作为最起码的工作示例，我们可以基于官方的 ubuntu 码头容器图像构建一个 `lolcow` 容器。 将以下内容放入 `lolcow.def` 文件(基于 [独特性文档](https://www.sylabs.io/guides/3.2/user-guide/build_a_container.html))：
```
sudo sidularity building lolcow.simg lolcow.def
```

这个“recipe”使用停靠图像作为基础 (`ubuntu`), 安装一些 `apt` 软件包，修改一些环境变量， 并指定 `运行脚本` (使用 `独一无二性运行` 命令执行)。 单一性定义文件格式的详细信息可在官方的 [文档](https://www.sylabs.io/docs/) 中找到。

(rr-renv-containers-sinularity-storage)=

```
单纯性运行lolcow.simg
```

这将从 DockerHub 拉取ubuntu 图像， 在定义文件中运行配方的步骤并生成单一输出图像文件(`lolcow)。 img`)。 最后执行 `运行脚本`

```
singularity run lolcow.simg
```

理想的情况是，你应该看到一个漂亮的 ASCII 母牛和几个智慧词：

```
___________________________________
/ 您将被请求来帮助疑难中的一个 \
的朋友。                /
-----------------------------------
       \   ^__^
        \  (oo)\_______
           (__)\       )\/\
               ||----w |
               ||     ||
```

HPC兼容，单一性容器也得到各种工作流程管理工具的支持。 例如， [吸附](https://snakemake.readthedocs.io/en/stable/) 和 [下一步流动](https://www.nextflow.io/docs/latest/singularity.html) 都支持针对工作的唯一性容器。 这使得独特的容器特别适合于使用广泛使用的 [slurm](https://slurm.schedmd.com/documentation.html) 工作量管理器来平行处理高清系统上的工作流程。 使用单一性、容器和快照/下流是一种将可再生产量降到大规模的方法。 此外，作为一种额外的益处，将桌面机器的工作流程带到高清系统不再需要自定义作业提交脚本。

(rr-renv-containers-singularity-storage)=
### Long-term Storage of Container Images

必须指出，仅仅是一个集装箱配方文件本身并不是可以复制的，因为构建过程取决于各种(在线)来源。 因此，如果基础源更新，相同的配方文件可能会导致不同的图像。

要实现真正的可复制性，必须存储实际容器 _图像_。 对于独一无二的图像，这样做特别容易，因为图像只是一个大的文件。 它们的大小可能各不相同，从几十个兆字节（微型容器）到几个千兆字节不等。 因此不适合存储在 git 存储库本身 免费， 存储容器图像的可接受和长期解决办法是

zenodo。 Since zenodo mints DOIs for all content uploaded, the images are immediately citable. 与 [Docker Hub](https://hub.docker.com/) 相反(它也只接受停泊器图像)， zenodo还通过一个复杂的元数据系统明确地面向长期储存和发现。 因此，它最适合于储存与具体分析有关的科学集装箱，因为这些集装箱往往不会随着时间的推移而变化。</p> 

(rr-renv-containers-warning)=


## Words of Warning

尽管单一性和码头看起来类似，但它们在概念上是非常不同的。 除了单一性不需要Root访问运行的容器这一显而易见的事实， 它还以不同方式处理主机和集装箱文件系统之间的区别。 例如，在默认情况下，单一性包括容器中的几个绑定点，即：

- `$HOME`
- `/sys:/sys`
- `/proc:/proc`
- `/tmp:/tmp`
- `/var/tmp:/var/tmp`
- `/etc/resolv.conf:/etc/resolv.conf`
- `/etc/passwd:/etc/passwd`
- `$PWD`

注意, `$PWD` 很方便，因为它意味着工作目录中的所有文件都是在容器中可见的。 然而，默认情况下绑定 `$HOME` 还意味着使用来自 `$HOME` 的配置文件的软件可能出乎意料，因为图像特定的配置文件被当前用户设置覆盖在 `$HOME` 中。 虽然这种行为在高温热吸附器的情况下很简单，但是这种行为对于可再生产的研究来说是潜在危险的。 为了避免潜在的问题，任何安装在单一性容器中的软件都应指向一个全球性的、独立于用户的配置文件。
