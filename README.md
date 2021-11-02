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

```docker ps -a```

To check more information check below commands:

```console
docker --version
docker version
docker info
```
