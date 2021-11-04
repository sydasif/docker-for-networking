# Docker for Networking

A container is a standard unit of software that packages up code and all its dependencies so the application runs quickly and reliably from one computing environment to another. A Docker container image is a lightweight, standalone, executable package of software that includes everything needed to run an application: code, runtime, system tools, system libraries and settings. See more information on [what is a container](https://www.docker.com/resources/what-container)?

## Docker Installation on Ubuntu

You can install Docker Engine in different ways, depending on your needs.

### Install using the repository

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

* Update the apt package index, and install the latest version of Docker Engine and containerd, or go to the next step to install a specific version:

```console
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

* Verify that Docker Engine is installed correctly by running the hello-world image.

```console
sudo docker run hello-world
```

See other ways to [Install Docker Engine](https://docs.docker.com/engine/install/).

### Docker Commands

The hello_world container will still exist on your system, as can be viewed by running this command:

```console
docker ps -a
```

To check more information about docker use below commands:

```console
docker --version
docker version
docker info
```

To pull image from docker hub:

```con
ubuntu@ubuntu:~$ docker pull ubuntu
Using default tag: latest
latest: Pulling from library/ubuntu
Digest: sha256:626ffe58f6e7566e00254b638eb7e0f3b11d4da9675088f4781a50ae288f3322
Status: Image is up to date for ubuntu:latest
docker.io/library/ubuntu:latest

ubuntu@ubuntu:~$ docker pull centos
Using default tag: latest
latest: Pulling from library/centos
Digest: sha256:a27fd8080b517143cbbbab9dfb7c8571c40d67d534bbdee55bd6c473f432b177
Status: Image is up to date for centos:latest
docker.io/library/centos:latest
```

To list install docker images:

```con
ubuntu@ubuntu:~$ docker image ls
REPOSITORY                    TAG       IMAGE ID       CREATED        SIZE
ubuntu                        latest    ba6acccedd29   2 weeks ago    72.8MB
centos                        latest    5d0da3dc9764   6 weeks ago    231MB

ubuntu@ubuntu:~$ docker images
REPOSITORY                    TAG       IMAGE ID       CREATED        SIZE
ubuntu                        latest    ba6acccedd29   2 weeks ago    72.8MB
centos                        latest    5d0da3dc9764   6 weeks ago    231MB

```

To start and tty a container and check os:

```con
ubuntu@ubuntu:~$ docker start 6b4033592308 
6b4033592308

ubunt@ubuntu:~$ docker ps 
CONTAINER ID   IMAGE     COMMAND   CREATED         STATUS         PORTS     NAMES
6b4033592308   ubuntu    "bash"    7 minutes ago   Up 3 seconds             wonderful_goldstine

ubuntu@ubuntu:~$ docker attach 6b4033592308

root@6b4033592308:/# 
root@6b4033592308:/# cat /etc/os-release 
NAME="Ubuntu"
VERSION="20.04.3 LTS (Focal Fossa)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 20.04.3 LTS"
VERSION_ID="20.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=focal
UBUNTU_CODENAME=focal
root@6b4033592308:/#
```
