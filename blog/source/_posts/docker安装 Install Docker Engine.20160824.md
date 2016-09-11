
---
title: docker安装 Install Docker Engine
permalink: docker安装 Install Docker Engine
comments: true
date: 2016-08-24 23:30:00
toc: true
tags:
   - Docker 学习
description: Docker 是一个开源的应用容器引擎，让开发者可以打包他们的应用以及依赖包到一个可移植的容器中，然后发布到任何流行的 Linux 机器上，也可以实现虚拟化。容器是完全使用沙箱机制，相互之间不会有任何接口。
---
&emsp;&emsp; Docker 是一个开源的应用容器引擎，让开发者可以打包他们的应用以及依赖包到一个可移植的容器中，然后发布到任何流行的 Linux 机器上，也可以实现虚拟化。容器是完全使用沙箱机制，相互之间不会有任何接口。
<!-- more -->





##  docker安装 Install Docker Engine
### docker安装 Install Docker Engine

#### **前言：**

>  运行任何应用程序，都需要有两个基本步骤：构建一个镜像、运行容器。

  >  这些步骤都是从Docker Client的命令开始的。

 >   第1步：构建镜像

>  如前所述，Docker Image是一个构建容器的只读模板，它包含了容器启动所需的所有信息，包括运行程序和配置数据。

>    每个镜像都源于一个基本的镜像，然后根据Dockerfile中的指令创建模板。对于每个指令，在镜像上创建一个新的层面。

>    第2步：运行容器

>  运行容器源于我们在第一步中创建的镜像。当容器被启动后，一个读写层会被添加到镜像的顶层。当分配到合适的网络和IP地址后，需要的应用程序就可以在容器中运行了。

 >   接下来，让我们一起安装Docker！

#### ubuntu 系列安装docker 

``` 
➜  ~ uname -r
4.4.0-31-generic
➜  ~  sudo lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial
➜  ~ file /sbin/init
/sbin/init: symbolic link to /lib/systemd/systemd
➜  ~ file /lib/systemd/systemd
/lib/systemd/systemd: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 2.6.32, BuildID[sha1]=dfc32dfa86e4694a0408bd227e8f91d2acbbc11a, stripped
➜  ~ 
```

##### docker安装：
第一种方式：

操作系统默认的apt源有docker包，我们可以直接使用下面的apt-get命令安装docker:

``` $ sudo apt-get install -y docker.io```

但是ubutun仓库自带的往往不是最新的；为了获取最新的docker使用curl

第二种方式：

网站 https://get.docker.com 提供了curl-able的安装脚本install.sh，我们可以通过curl的方式进行安装docker。

我们先安装curl:
```$ sudo apt-get update```
``` $ sudo apt-get install curl```

然后进行docker的安装：

``` $ curl -k -sSl https://get.docker.com | sudo sh```

查看docker版本：

``` $ docker version```

```
Client:
 Version:      1.11.2
 API version:  1.23
 Go version:   go1.6.2
 Git commit:   b9f10c9
 Built:        Thu, 16 Jun 2016 21:17:51 +1200
 OS/Arch:      linux/amd64
Cannot connect to the Docker daemon. Is the docker daemon running on this host?
➜  ~
  ```

 建议使用第二种方式；
``` sudo docker run hello-world```
``` 
➜  ~ sudo docker run hello-world

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker Hub account:
 https://hub.docker.com

For more examples and ideas, visit:
 https://docs.docker.com/engine/userguide/  
```

#### 补充命令：可以使用命令查看容器状态补充命令：可以使用命令查看容器状态

1、查看正在运行的容器

``` sudo docker ps```

2、查看所有的容器

``` sudo docker ps -a ```

3、查看本地镜像

```sudo docker images```

 4、从镜像中运行/停止一个新实例

``` sudo docker run/stop --help ```

**注意：**

每次 使用docker命令都需要使用sudo

这里把当前用户加入到docker组就可以直接使用命令，而不用每次都加sudo

``` sudo groupadd docker```


改完后需要重新登陆用户

$ ```sudo gpasswd -a ${USER} docker```

### 使用镜像发布新的容器

最后使用上面下载下来的镜像发布一个新的Docker容器.下面的命令会发布一个新的容器并且可以使用/bin/bash进入查看.

``` docker run -i -t ubuntu /bin/bash```
如果要从docker container推出的话按下 CTRL + P + Q. 这会让容器背景执行，输出信息到console去。如果你终止了console的话当前容器就会终止运行.

验证完所有的Docker容器之后，使用下面的命令再词列举下正在运行的容器.

**# docker ps**
```
CONTAINER ID     IMAGE     COMMAND        CREATED        STATUS        PORTS    NAMES
f2582758af13     ubuntu    "/bin/bash"    2 hours ago    Up 2 hours             first_ubuntu
默认情况下上面的命令只会列出当前所有正在运行的containers. 如果要列出全部的容器(包含停止了的)那就使用这个命令.
```
**# docker ps -a**
启动/停止/进入Container

使用下面的命令你可以启动停止和进入到任何的容器去，启动

**# docker start < CONTAINER ID>**
停止

**# docker stop < CONTAINER ID>**
进入任何正在允许的容器命令


----------


**# docker attach < CONTAINER ID>**
