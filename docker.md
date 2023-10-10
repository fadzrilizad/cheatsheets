# Docker

## Why use docker

- Easy to install and run software without worrying setup/dependencies

## What is docker

- Platform/ecosystem around creating and running container

## Image

- Contain all dependencies/config required to run a program
- File system snapshot
- And start up command to start program
- Each program start will be instance/running process

## Container

- Instance of images
- Running program
- Isolated set of hardware resources
- Each OS has kernel (running software process)
- It govern program to hardware access
- It interact using System Call
- Important when we need program that our OS don't support that version
- Use OS system **Namespacing**
- It look all the resources, and segment out portion of resources
- Container = running process + hardware resources

#### Namespacing

- Isolate resources to group of processes
- If process ask for resources
- It will direct to specific area of given hardware
- Also can use for software element

#### Control group

- Limit amount of resources
- That particular process can use

## Docker for Windows/Mac

- Docker client
  - Docker CLI
  - Connect to docker sever
- Docker server
  - Docker Server
  - Creating container
  - Creating images
  - Maintaining containers
  - Upload images

## Install Docker

- [Link](https://docs.docker.com/desktop/)

## How docker run behind the scene

- `docker run hello-world` -> docker cli
- Docker cli -> docker server
- Docker server check if it has local copy (image cache)
- If not found, look at the docker hub
- If docker hub found what we are looking
- Download to your computer (image cache)
- After download use image to create instance
- Container run the program

## How docker run on computer

- System Namespacing and Control groups
- Specific to the Linux OS (specific feature)
- When install docker for Windows & Mac
- It install with linux VM
- When docker run, linux VM run
- Check `docker version` in `Server`
- We can see OS is Linux

## Docker run

- `docker` `run` `<img name>`
- `docker` refer to docker client
- `run` create and run container
- `<img name>` name of image to use for this container
- When `run` not only get snapshot, also default command
- Can override the default command
- `docker run <img name> command!`
- `command!` will override default command
- For example `docker run busybox echo hi there`
- `docker run busybox ls` list all the file/directory in root
- Root are not in our computer, it inside container
- In `hello-world` not have file system like busybox
- `docker run hello-world ls` will output error

## Docker Command

- `docker version` check docker version
- `docker run hello-world` install docker hello word
