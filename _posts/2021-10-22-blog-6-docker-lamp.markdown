---
layout: post
title:  "Blog 6 - Docker-Compose: LAMP Stack"
date:   2021-10-22 9:59:31 -0700
categories: jekyll update
---

# **Intro**
In this blog post, I'll be talking briefly about what a LAMP stack is, what Docker and Docker-Compose are, and finally how to install Docker and Docker-Compose in preparation for next week's blog. 

# **LAMP Stack**
![LAMP stack](/assets/lamp-stack.png)


I'm pretty sure that by now you've heard of a LAMP stack before. In the odd case that you haven't, let's talk about it briefly. A LAMP stack is comprised of 4 software components. When put together in layers, which each take care of a specific need, you get a set of software needed to run a complete web server. Let's take a look at each of the parts:
- **L**inux
    - The first layer is the operating system that holds up the entire stack. All the other layers rely and run on top of the OS.
- **A**pache
    - This is the second layer which runs the actual web server software.
- **M**ySQL
    - The third layer is the database. This stores all the data that the web server queries to get all its information from.
- **P**HP
    - The fourth and final layer is the LAMP's programming language. PHP is a server-side scripting language used for web development. It runs on top of all the other layers.

As a sidenote, there are many other types of web server stacks that have gained more and more popularity over the years. One such example is the MEAN stack (MongoDB, Express, Angular, and Node). A reason to use a MEAN stack is that it's much more dynamic than a traditional, static LAMP.

# **Docker and Docker-Compose**
<img src="/assets/docker-logo.png" alt="Docker logo" width="400px" height="100px"/> 
<img src="/assets/docker-compose-logo.png" alt="Docker-Compose logo" width="215px" height="150px"/>

Docker, one of the first in the wave of innovation that is containerization technology. The introduction of Docker is what really popularized the use of containers. Containerization is simply a form of virtualization. To see the difference between virtual machines and containers, take a look at the graphic below.

![Containers vs VMs](/assets/containers-vs-vms.png)

With VMs, you isolate each application with its own guest OS and binaries/libraries. The VMs run on top of the host's hypervisor. With containers, you isolate each application with its own binaries and libraries; guest OSes aren't given to each application. The containers run on top of Docker's container engine. Thus, containers are much smaller and easily deployable since they don't need to be packaged with their own OS. You just need to have Docker installed in order to run any container.

Docker-Compose takes Docker to the next level by being able to create multiple containers at the same time, allowing you to run multi-container Docker applications. With a single command, you can spin up a 2-tier LAMP stack. This is actually what we'll be doing in next week's blog!

# **Installation**
Docker is currently available on Mac, Windows, and Linux. The desktop application is available natively on Mac and Windows, but they [recently announced](https://www.docker.com/blog/accelerating-new-features-in-docker-desktop/) that Docker Desktop for Linux has been made a higher priority on their roadmap. 

Go to https://docs.docker.com/get-docker/ and get the right download depending on your OS. Be careful about system requirements, especially for Windows. You need to have at least Windows 10 *Pro* to be able to run Docker Desktop. I also recommend downloading [WSL](https://docs.microsoft.com/en-us/windows/wsl/install) (Windows Subsystem Linux) and having Docker use the WSL2 backend instead of Hyper-V for virtualization. It's apparently more efficient, and if you also use VirtualBox, you don't have to swap between using Docker and switching on Hyper-V and using VirtualBox and switching it off.

If you installed Docker on Linux, be sure to also download Docker-Compose. It's a separate package that's not part of the regular docker install.

```
$ sudo apt update 
$ sudo apt install docker-compose -y
```

# **Next Week**
Don't miss the next blog. I'll be going over a project where I installed a 2-tier containerized LAMP stack using Docker-Compose. It'll be a lot of fun!

# **More Info**
[Docker Docs](https://docs.docker.com/)

[Docker Compose Install](https://docs.docker.com/compose/install/)