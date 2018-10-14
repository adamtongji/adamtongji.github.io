---
layout: post  
title: Docker一键安装wordpress  
categories: [Docker, network]  
description: docker学习和使用案例  
keywords: docker, wordpress  
---

## Docker应用之一键化安装Wordpress(无需代码基础)

WordPress是使用PHP语言开发的博客平台，用户可以在支持PHP和MySQL数据库的服务器上架设属于自己的网站。也可以把 WordPress当作一个内容管理系统（CMS）来使用。Wordpress的搭建和维护基本只需鼠标操作、无需代码和网页开发的基础，很多博客爱好者使用wordpress作为自己快速搭建个人博客的平台，一些公司也使用wordpress来搭建公司的官方网站(如下图示例)。  
![wordpress示例](/images/2018-10-14/ex1.png)  

尽管wordpress功能强大且操作方便，安装Wordpress软件仍需对系统、网络以及数据库有一定的了解，并且安装过程可能会对一些系统原本配置(比如Mysql)产生一定影响，不同的系统安装方法也有一定差别。安装Worpress成为使用Wordpress平台主要的门槛。  

### Docker简介
Docker是一款功能强大的容器化软件，能够创建一个同原本系统相隔离的环境，来运行软件、网站等等。Docker的安装也是非常方便的。在Windows和Mac系统，docker提供了docker桌面版([https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop))，和安装常规软件无差别。  
对于Linux用户，比如在个人工作站或者各类云服务器（阿里云、腾讯云等），通过系统自身软件管理器(yum,apt-get等)即可快速安装，下以centos为例：
```Bash
sudo yum install -y yum-utils \
  device-mapper-persistent-data \
  lvm2
sudo yum-config-manager \
   --add-repo \
   https://download.docker.com/linux/centos/docker-ce.repo
sudo yum install docker-ce
```

### 用Docker搭建Wordpress
有了Docker，我们便可以快速安装Wordpress。首先，Win用户和Mac用户打开Docker软件，Linux用户启用Docker服务。其次，创建一个文件夹，并新建一个文档，命名为“docker-compose.yml”。第三步，将以下配置复制入刚创建的yml文件。
```YAML
version: "3"
services:
  mariadb:
    image: mariadb
    environment:
      MYSQL_ROOT_PASSWORD: root
      MYSQL_DATABASE: wordpress
    volumes:
      - mariadata:/var/lib/mysql
    networks:
      - my-bridge
  wordpress:
    image: wordpress
    ports:
      - 8080:80 # 如果8080被占用，修改8080为任意其他端口
    environment:
      WORDPRESS_DB_HOST: mariadb
      WORDPRESS_DB_PASSWORD: root
    networks:
      - my-bridge
    depends_on:
      - mariadb
volumes:
  mariadata:
    driver: local
networks:
  my-bridge:
    driver: bridge
```
第四步，在该文件夹下打开命令行，输入`docker-compose up`，此时Wordpress和Mysql便自动下载并安装入Docker容器，根据网速不同等待一些时间便安装完成。最后，打开你的浏览器，输入"localhost:8080"或者"localhost"或者"127.0.0.1"，远程服务器的直接输入服务器IP地址，即可进入Wordpress安装界面，开始你的Wordpress之旅。  

好了，或许你已经安装好了，那么如何卸载/中止Wordpress服务呢？也很简单，首先进入你的文件夹，输入：
```Bash
docker-compose down
```
然后，docker便会逐步停止所有相关服务，同卸载有相同效果。如需再度安装使用Wordpress，则在相同文件夹再输入`docker-compose up`或者`docker-compose up -d`运行于后台。

综上，无论是Windows,Mac还是Linux，只要有docker便可以实现很多原本很困难的功能，比如`docker-compose up`命令便可以一键安装多个功能和组件的Wordpress平台。欢迎留言讨论Docker相关的问题~
