# Docker for Networking

**Docker:** Docker is software that runs on Linux and Windows. It creates, manages, and can even orchestrate containers.The software is currently built from various tools from the open-source project

**containers:** A container is a standard unit of software that packages up code and all its dependencies so the application runs quickly and reliably from one computing environment to another.

A Docker container image is a lightweight, standalone, executable package of software that includes everything needed to run an application: code, runtime, system tools, system libraries and settings. See more information on [what is a container](https://www.docker.com/resources/what-container)?

## The Docker technology

When most people talk about Docker, they’re referring to the technology that runs containers. However, there are at least three things to be aware of when referring to Docker as a technology:

1. _The runtime_
2. _The daemon (a.k.a. engine)_
3. _The orchestration_

## Windows containers vs Linux containers

It’s vital to understand that a running container shares the kernel of the host machine it is running on. Its means that a containerized Windows app will not run on a Linux-based Doer host, and vice-versa. Windows containers require a Windows host, and Linux containers require a Linux host.

It is possible to run Linux containers on Windows machines. For example, Docker Desktop running on Windows has two modes — “Windows containers” and “Linux containers”. Depending on your version of Docker Desktop, Linux container run either inside a lightweight Hyper-V VM or using the Windows Subsystem for Linux (WSL). The WSL option is newer and the strategic option for the future as it doesn’t require a Hyper-V VM and oﬀers better performance and compatibility.

## Docker Installation

You can install [Docker Engine](https://docs.docker.com/engine/install/) in different ways, depending on your needs.

### Installing Docker on Linux

In this lab we’ll look at one of the ways to install on Ubuntu Linux 20.04 LTS.

Before you install Docker Engine for the first time on a new host machine, you need to set up the Docker repository. Afterward, you can install and update Docker from the repository.

### Set up the repository

* Update the apt package index and install packages to allow apt to use a repository over HTTPS:

```console
$ sudo apt-get update

$ sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```

* Add Docker’s official GPG key:

```console
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

* Use the following command to set up the stable repository.

```console
$ echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

### Install Docker Engine

* Update the apt package index, and install the latest version of Docker Engine and container, or go to the next step to install a specific version:

```console
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

* Verify that Docker Engine is installed correctly by running the hello-world image.

```console
sudo docker run hello-world
```

See other ways to [Install Docker Engine](https://docs.docker.com/engine/install/).

## Docker Commands

Docker is now installed and you can test running some commands to check more information about docker.

```console
sudo docker --version
sudo docker version
sudo docker info
```

## Docker Images

It’s useful to think of a Docker image as an object that contains an OS ﬁle system, an application, and all application dependencies. As a virtual machine template is a stopped virtual machine. In the Docker world, an image is effectively a stopped container.

* Run the _docker image ls_ command

```console
~ » docker image ls
REPOSITORY   TAG       IMAGE ID       CREATED       SIZE
```

* Getting images onto your Docker host is called “pulling”.

```console
ubuntu@ubuntu:~$ docker pull ubuntu:latest
Using default tag: latest
latest: Pulling from library/ubuntu
Digest: sha256:626ffe58f6e7566e00254b638eb7e0f3b11d4da9675088f4781a50ae288f3322
Status: Image is up to date for ubuntu:latest
docker.io/library/ubuntu:latest
```

* To list install docker images:

```con
$ docker image ls
REPOSITORY                    TAG       IMAGE ID       CREATED        SIZE
ubuntu                        latest    ba6acccedd29   2 weeks ago    72.8MB
```

```con
$ docker images
REPOSITORY                    TAG       IMAGE ID       CREATED        SIZE
ubuntu                        latest    ba6acccedd29   2 weeks ago    72.8MB
```

## Docker Containers

Now that we have an image pulled locally, we can use the _docker container run_ command.

```con
$ docker container run -it ubuntu:latest /bin/bash
root@20e3b1f9bab4:/#
```

docker container run command tells the Docker daemon to start a new container. the -it ﬂags tell Docker to make the container interactive and to attach the current shell to the container’s terminal. Next, the command tells Docker that we want the container to be based on the ubuntu:latest image. Finally, we tell Docker which process we want to run inside of the container.

Press _Ctrl+PQ_ to exit the container without terminating it. This will land your shell bash at the terminal of your Docker host.

You can see all running containers on your system using the _docker container ls_ command.

```con
$ docker container ls
20e3b1f9bab4   ubuntu:latest   "/bin/bash"   11 minutes ago   Up 11 minutes             frosty_williams
```

Or

```con
~ » docker ps
CONTAINER ID   IMAGE           COMMAND       CREATED          STATUS          PORTS     NAMES
20e3b1f9bab4   ubuntu:latest   "/bin/bash"   11 minutes ago   Up 11 minutes             frosty_williams
```

### Attaching to running containers

You can attach your shell to the terminal of a running container with the _docker container exec_ command. As the container from the previous steps is still running.

```con
~ » docker container exec -it frosty_williams bash
root@20e3b1f9bab4:/# ls
bin  boot  dev  etc  home  lib  lib32  lib64  libx32  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
root@20e3b1f9bab4:/# 
```

Or

```con
~ » docker attach frosty_williams
root@20e3b1f9bab4:/# ls
bin  boot  dev  etc  home  lib  lib32  lib64  libx32  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
root@20e3b1f9bab4:/# 
```

We can also use _CONTAINER ID_ instead of _NAMES_ in above command.

Exit the container again by pressing _Ctrl-PQ_.

Stop the container and kill it using the docker _container stop_ and _docker container rm_ commands.

```con
docker container stop frosty_williams
frosty_williams
```

```con
docker container rm frosty_williams
frosty_williams
```
