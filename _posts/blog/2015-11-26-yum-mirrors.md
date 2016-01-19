---
layout: post
title: 修改CentOS默认yum源为国内yum镜像源
category: blog
description: 修改CentOS默认yum源为mirrors.163.com或者mirrors.aliyun.com
---
有时候CentOS默认的yum源不一定是国内镜像，导致yum在线安装及更新速度不是很理想。这时候需要将yum源设置为国内镜像站点。国内主要开源的开源镜像站点应该是网易和阿里云了。
### 修改CentOS默认yum源为mirrors.163.com
1、首先备份系统自带yum源配置文件/etc/yum.repos.d/CentOS-Base.repo

    [root@localhost ~]# mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup
2、进入yum源配置文件所在的文件夹

    [root@localhost ~]# cd /etc/yum.repos.d/
3、下载163的yum源配置文件到上面那个文件夹内

**CentOS7**

    [root@localhost yum.repos.d]# wget http://mirrors.163.com/.help/CentOS7-Base-163.repo 

**CentOS6**

    [root@localhost yum.repos.d]# wget http://mirrors.163.com/.help/CentOS6-Base-163.repo 

**CentOS5**

    [root@localhost yum.repos.d]# wget http://mirrors.163.com/.help/CentOS5-Base-163.repo
4、运行yum makecache生成缓存

    [root@localhost yum.repos.d]# yum makecache
5、这时候再更新系统就会看到以下mirrors.163.com信息

    [root@localhost yum.repos.d]# yum -y update
    已加载插件：fastestmirror, refresh-packagekit, security
    设置更新进程
    Loading mirror speeds from cached hostfile
    * base: mirrors.163.com
    * extras: mirrors.163.com
    * updates: mirrors.163.com
### 修改CentOS默认yum源为mirrors.aliyun.com

1、首先备份系统自带yum源配置文件/etc/yum.repos.d/CentOS-Base.repo

    [root@localhost ~]# mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup
2、下载ailiyun的yum源配置文件到/etc/yum.repos.d/

**CentOS7**

    [root@localhost ~]# wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo 

**CentOS6**

    [root@localhost ~]# wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-6.repo 

**CentOS5**

     [root@localhost ~]# wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-5.repo 
3、运行yum makecache生成缓存

    [root@localhost ~]# yum makecache
4、这时候再更新系统就会看到以下mirrors.aliyun.com信息

    [root@localhost ~]# yum -y update
    已加载插件：fastestmirror, refresh-packagekit, security
    设置更新进程
    Loading mirror speeds from cached hostfile
    * base: mirrors.aliyun.com
    * extras: mirrors.aliyun.com
    * updates: mirrors.aliyun.com