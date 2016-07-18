# dockerstartertest
## Introduction
This “how to” is intended to be followed strictly. At first it will appear to be very confusing and may seems like unnecessarily complicated. It is confusing as we will be dealing with virtual machine inside a virtual machine all of which will be hosted on top of Windows. A successful test result at the end and inline explanation would clear some of the confusion. A walkthrough and question and answer session regarding the setup will probably be necessary to clear any remaining confusions. We would use a bare minimum Apache Docker image and just a single static html page as our project to demonstrate Docker in this tutorial. 

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
``` $ docker run hello-world ```

- A successful run of hello-world project will produce a screen similar to this one

![Docker hello world](/img/015_docker-hello-world.png)


##Prepare Project Folder

For this tutorial we would assume our project folder is located at drive D: . Let us create a project folder using Windows Explorer as shown below.
```bash
D:\Projects\BitBrush\
```

## Clone Git Project
Open "Docker Quickstart Terminal". Change directory to /d/Projects/BitBrush

Clone test Git project using the following command. You can also use any other Windows Git client like TortoisGit or SourceTree.
```bash
$ git clone https://github.com/BitBrushCo/dockerstartertest.git
```


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

