---
title: "Docker Architecture: Why is it important?"
datePublished: Sat May 04 2024 07:51:12 GMT+0000 (Coordinated Universal Time)
cuid: clvrt1ovm00000al64lywb7mg
slug: docker-architecture-why-is-it-important
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1714809059938/41ac8f8a-b8e3-4245-a82a-0ce693692273.png
tags: docker

---

Many of us believe that Docker is an integral part of DevOps. So **there must be an amazing architecture** behind this incredible **tool.** In this article , I will **tell you** everything you **need to** know about Docker architecture

## Docker vs. Conventional Virtualization

### A VM (Virtual Machine) is what?

A virtual machine (VM) simulates a physical server. A virtual machine uses the physical hardware of the computer to replicate the identical setting in which you would install your apps. You can utilize a system virtual machine (which runs a whole OS as a process, allowing you to replace a real machine with a virtual machine), or process virtual machines, which enable you to run individual computer applications in the virtual environment, depending on your use case.

### What is Docker?

Docker is an open-source project that offers a software development solution known as containers. To understand Docker, you need to know what containers are. According to *Docker,* a container is a lightweight, stand-alone, executable package of a piece of software that includes everything needed to run it.

Containers are platform-independent and hence Docker can run across both Windows and Linux-based platforms. The main purpose of Docker is that it lets you run microservice applications in a distributed architecture.

When compared to Virtual machines, the Docker platform moves up the abstraction of resources from the hardware level to the Operating System level. This allows for the realization of the various benefits of Containers e.g. application portability, infrastructure separation, and self-contained microservices.

![](https://media.licdn.com/dms/image/D5612AQEJfYMgqog0YA/article-inline_image-shrink_1500_2232/0/1694887014680?e=1720051200&v=beta&t=8M1giJ_uYaAKF6oOKX8QmiHidJXIkaN14NhzDrc4sgk align="left")

### Docker’s Workflow

First, let us look take a look at Docker Engine and its components so we have a basic idea of how the system works. Docker Engine allows you to develop, assemble, ship, and run applications using the following components:

1. **Docker Daemon**: A persistent background process that manages Docker images, containers, networks, and storage volumes. The Docker daemon constantly listens for Docker API requests and processes them.
    
2. **Docker Engine REST API**: An API is used by applications to interact with the Docker daemon. It can be accessed by an HTTP client.
    
3. **Docker CLI**: A command-line interface client for interacting with the Docker daemon. It significantly simplifies how you manage container instances and is one of the key reasons why developers love using Docker.
    

![](https://media.licdn.com/dms/image/D5612AQFc3OnIOTbCVA/article-inline_image-shrink_1500_2232/0/1694886813070?e=1720051200&v=beta&t=wBI7PJ_DRm-Kudqg-7QWHWgIyeexSoNMawuxvy8D_pQ align="left")

At first, Docker client talks to the Docker daemon, which performs the heavy lifting of the building, running, as well as distributing our Docker containers. Fundamentally, both the Docker client and daemon can run on the same system. We can also connect a Docker client to a remote Docker daemon. In addition, by using a REST API, the Docker client and daemon, communicate, over UNIX sockets or a network interface.

### Docker Architecture

The architecture of Docker uses a client-server model and consists of the Docker’s Client, Docker Host, Network and Storage components, and the Docker Registry/Hub. Let’s look at each of these in some detail.

### Docker’s Client

Docker users can interact with Docker through a client. When any docker commands runs, the client sends them to dockerd daemon, which carries them out. Docker API is used by Docker commands. It is possible for Docker client to communicate with more than one daemon.

### Docker Host

The Docker host provides a complete environment to execute and run applications. It comprises of the Docker daemon, Images, Containers, Networks, and Storage. As previously mentioned, the daemon is responsible for all container-related actions and receives commands via the CLI or the REST API. It can also communicate with other daemons to manage its services.

### Docker Objects

### 1\. Images

Images are nothing but a read-only binary template that can build containers. They also contain metadata that describe the container’s capabilities and needs. Images are used to store and ship applications.

### 2\. Containers

Containers are sort of encapsulated environments in which you run applications. Container is defined by the image and any additional configuration options provided on starting the container, including and not limited to the network connections and storage options. Containers only have access to resources that are defined in the image, unless additional access is defined when building the image into a container.

### 3\. Networks

Docker networking is a passage through which all the isolated container communicate. There are mainly five network drivers in docker:

1. **Bridge**: It is the default network driver for a container. You use this network when your application is running on standalone containers, i.e. multiple containers communicating with the same docker host.
    
2. **Host**: This driver removes the network isolation between docker containers and docker host. You can use it when you don’t need any network isolation between host and container.
    
3. **Overlay**: This network enables swarm services to communicate with each other. You use it when you want the containers to run on different Docker hosts or when you want to form swarm services by multiple applications.
    
4. **None**: This driver disables all the networking.
    
5. **Macvlan**: This driver assigns mac address to containers to make them look like physical devices. It routes the traffic between containers through their mac addresses.
    

### 4\. Storage

You can store data within the writable layer of a container but it requires a storage driver. Being non-persistent, it perishes whenever the container is not running. Moreover, it is not easy to transfer this data. With respect to persistent storage, Docker offers four options:

* **Data Volumes**: They provide the ability to create persistent storage, with the ability to rename volumes, list volumes, and also list the container that is associated with the volume.
    
* **Volume Container**: It is an alternative approach wherein a dedicated container hosts a volume and to mount that volume to other containers.
    
* **Directory Mounts**: Another option is to mount a host’s local directory into a container.
    
* **Storage Plugins**: Storage Plugins provide the ability to connect to external storage platforms.
    

**Docker’s Registry**

Docker registries are services that provide locations from where you can store and download images. In other words, a Docker registry contains Docker repositories that host one or more Docker Images. Public Registries include two components namely the Docker Hub and Docker Cloud. You can also use Private Registries. The most common commands when working with registries include: docker push, docker pull, docker run