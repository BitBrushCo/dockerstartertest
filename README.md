# dockerstartertest
## Introduction
This "how to" will show how to install Docker in a Windows machine with a super simple staic web site. We will use a simple Docker image for Apache.

## Software Installs

### Install Git for Windows
Install [Git for Windows project](https://git-for-windows.github.io/). I don't remember clearly but Docker may complain about not finding 'ssh' command. If it complained then install Git for Windows project and have Git binaries in your Windows "PATH" enviornment varialbe.

### Install Oracle VirtualBox
Again I don't clearly remember if Docker will install VirtualBox for you or you will have to install VirtualBox prior to installing Docker ToolBox. To be on the safe side please install VirtualBox. If Docker ToolBox later insists on install VirtualBox just don't install it again.
Download and install [VirtualBox for Windows Host](https://www.virtualbox.org/wiki/Downloads)

## Install Docker with Docker ToolBox

- Download Docker ToolBox from [here](https://www.docker.com/products/docker-toolbox)
- Install Docker ToolBox
- Start "Docker Quickstart Terminal"

![Docker Terminal](/img/000_docker_terminal.png)

- Test Docker by running
> docker run hello-world

- A successful run of hello-world project will produce a screen similar to this one
![Docker hello world](/img/015_docker-hello-world.png)


## Prepare Project Folder

For this tutorial we would assume our project folder is located at drive D: . Let us create a project folder using Windows Explorer as shown below.

``` bash
 D:\Projects\BitBrush\
```

## Clone Git Project
Open "Docker Quickstart Terminal". Change directory to /d/Projects/BitBrush

Clone test Git project using the following command. You can also use any other Windows Git client like TortoisGit or SourceTree.
```bash
$ git clone https://github.com/BitBrushCo/dockerstartertest.git
```

## Share Windows Project Folder from VirtualBox
Open VirtualBox GUI. There should be a VM named "default". This is the VM created by Docker. This "default" VM acts the docker-machine which uses boot2docker to simulate Docker host machine. Docker containers run off of docker-machine. We will need to setup our project folder to be accessible by docker-machine. By default docker-machine (aka boot2docker) mount some specifically named shared folder if it finds them through VirtualBox's shared folder. More information about boot2docker and VirtualBox shared folder can be found [here](https://github.com/boot2docker/boot2docker#virtualbox-guest-additions). Here we are providing a excerpt related to shared folder.

> The first of the following share names that exists (if any) will be automatically mounted at the location specified:
> 1. Users share at /Users
> 2. /Users share at /Users
> 3. c/Users share at /c/Users
> 4. /c/Users share at /c/Users
> 5. c:/Users share at /c/Users

##

## Docker Run

- First make sure container has been stopped.
> docker stop $(docker ps -q)

- Remove container
> docker rm $(docker ps -aq)

- Run docker. This command is supposed to

 ``` bash
 docker run -it --rm --name myapache -p 8080:80 -v /Users/BitBrush/dockerstartertest:/usr/local/apache2/htdocs/ httpd:2.4
```
