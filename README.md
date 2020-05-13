# Docker and Kubernetes
[Link to Course](https://www.udemy.com/course/docker-and-kubernetes-the-complete-guide/https://www.udemy.com/course/docker-and-kubernetes-the-complete-guide/)

## Section 1
Why do we use Docker?
**Flow that we face and the problem Docker is going to fix**
- Download installer
- Run installer
- Error Message
- Troubleshoot
- rerun installer
- We still have a broken setup and are forced to start over

The above shows us the issue that all of us face when installing something new. How much time our time as engineers is wasted in a day on bullshit setup? Docker makes it like same to install and run software without worrying about dependencies

**What** is Docker?

Docker is an ecosystems' worth of tools
- Docker Client
- Docker Server
- Docker Machine
- Docker Images
- DockerHub
- Docker-Compose

Docker is a platform or ecosystem around creating and running containers.

Definitions:
**Image**: single file with all dependencies and config required to run a program

**Container**: Instance of an image

So a reference to "Docker" is a reference to the ecosystem.

## Using the Docker Client
```docker
docker run hello-world
```

The Docker CLI took our command `dkr hello-world` and passed it to the Docker client and then to the Docker server. The server looks in the image cache and, in my case, just ran the image. In the case that we don't have the image, the server reaches out to DockerHub and adds it to our cache. From here, the Container is created and shows us the hello world message from Docker.

## But really, what is a container?
To understand this, we need to understand the OS. Most machines have a kernel that governs how our computer behaves. We use a program like Chrome, Terminal, or Spotify. The programs make system calls that talk to the kernel. Those systems calls are thought of as functions.

Think of a situation that you have 2 programs on your machine that have nodejs and chrome. For both of them to run nodejs needs node needs python v2 and node needs python v3. So a way to handle this is through what is called **name spacing**.  Namespacing is when a segment of the hard drive has Python v2, and another section has Python v3 in this case. So the kernel, after getting the system call to run either program, reaches out to that segment and allows its use of that resource. Also, a more apt definition of namespace is the isolation of resources per process or group of processes. We also have control groups that are involved in namespaces called Control groups, which limit the number of resources used per process. So CGroups control things like memory,  and CPU.

So a **container** is a group of processes that have a grouping of resources explicitly allocated to it.

Behind the scenes, that image has a snapshot and startup command as a running process that uses system calls that talks to your kernel, and CGroups allocate out the resources and add a segment to your hard drive.

## How is Docker running on your machine
So the whole idea of CGroups and namespacing is Linux based terminology that unless you are running a Linux. If you are on Mac or Windows, what happens is when you installed Docker, you also installed a Linux Virtual Machine that runs as long as Docker is running. So you have running processes that hit the Linux kernel in Linux Virtual machine. The Linux Kernel handles the allocation of resources, and then you have access to that Container on your respective OS.