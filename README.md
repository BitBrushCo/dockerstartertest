# dockerstartertest
**IMPORTANT NOTE**
- Be specially careful about "CR" and "LF" in Windows formatted text files. If you have a shell script that was created in Windows environment, take special care to remove all "CR" from the file. Linux will not be able to run shell script if it contains "CR" character. Using Notepad++ you can convert Windows formatted file into Unix easily. Open Notepad++ and go to menu "Edit">"EOL Conversion">"UNIX/OSX Format".
- Careful about volume name path mapping between Windows and your virtual containers. Unix is case sensitive and Windows it not. When you declare volume information in "docker run" or in "docker-compose" commands use exact path with proper cases.

## Introduction
This "how to" will show how to install Docker in a Windows machine with a super simple staic web site. We will use a simple Docker image for Apache. The tutorial is very simple to follow and easy to build and test. Only major thing you have to be careful is about sharing folders between your hosts, guest and containers. The virtual path in this tutorial is relative to my directory settings in my Windows environment. It may be different in your environment. You should be able to add your own custom path just by changing the "-v" switch when you invoke ```docker run```. Everything else, including adding a shared volume in VirtualBox machine should be standard. There are a lot of different ways to share folders but my intention was to create a convention that would reduce developer's pain by eliminating modification to buld files and runner commands as much as possible.

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

- Run docker. This command is supposed to start a apache session. 

 ``` bash
 docker run -it --rm --name myapache -p 8080:80 -v /Users/BitBrush/dockerstartertest:/usr/local/apache2/htdocs/ httpd:2.4
```

- Test apache by opening a browser and trying out http://192.168.99.100:8080/

- This concludes a successful install test of Docker environment in your machine.
