# dockerstartertest
## Introduction
This “how to” is intended to be followed strictly. At first it will appears to be very confusing and may seems like unnecessarily complicated. It is confusing as we will be dealing with virtual machine inside a virtual machine all of which will be hosted on top of Windows. A successful test result at the end and inline explanation would clear some of the confusion. A walkthrough and question and answer session regarding the setup will probably be necessary to clear any remaining confusions. We would use a bare minimum Apache Docker image and just a single static html page as our project to demonstrate Docker in this tutorial. 


## Install Docker with Docker ToolBox

>  _to do_

##Prepare Project Folder

For this tutorial we would assume our project folder is located at drive D: . Let us create a project folder using Windows Explorer as shown below.
```bash
D:\Projects\BitBrush\
```

## Clone Git Project
Open "Docker Quickstart Terminal". Change directory to /d/Projects/BitBrush

Clone test Git project using the following command. You can also use any other Windows Git client like TortoisGit or SourceTree.
```bash
$ git clone https://iyusuf@github.com/BitBrushCo/dockerstartertest.git
```

A successful clone would just pull two files. README.md (this markdown file), and an html file named "index.html"



## Prepare Project Folder

## Clone GIT project

## Docker Run

- First make sure container has been stopped.
> docker stop $(docker ps -q)

- Remove container
> docker rm $(docker ps -aq)
  
- Run docker. This command is supposed to 
  
 ``` bash 
 docker run -it --rm --name myapache -p 8080:80 -v /Users/BitBrush/dockerstartertest:/usr/local/apache2/htdocs/ httpd:2.4
```

