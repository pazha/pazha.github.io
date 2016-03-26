---
layout: post
title: CentOS下LTMj环境搭建
category: blog
description: 关于Linux+Tomcat+MySQL+Java的Web服务环境搭建
---

**版本选择（仅供参考）：**

    CentOS6.7(Linux操作系统)
    Tomcat6(Web服务器)
    MySQL5.1（数据库）
    JDK1.7（编程语言）
**安装方式：**yum在线安装

**安装顺序：**CentOS→Tomcat→MySQL→JDK
### 第①步CentOS的安装与配置
从CentOS官网（www.centos.org）下载CentOS6.7DVD的ISO镜像文件。为了方便起见，这里我从阿里云镜像网站下载：

    http://mirrors.aliyun.com/centos/6.7/isos/x86_64/CentOS-6.7-x86_64-bin-DVD1.iso
下载完成之后，使用电脑店（u.diannaodian.com）或者老毛桃(www.laomaotao.org)把镜像刻录到U盘中，不会的请自行百度。刻录完成之后，进入主板BIOS设置U盘为第一启动。然后插入U盘，出现下面这个画面选择第一项便可以开始安装CentOS6.7了。![CentOS6.7](http://ww3.sinaimg.cn/mw690/9325ea4dgw1f03y4kucocj20fe080q5g.jpg)

图形化安装界面比较简单，具体安装步骤请自行百度或者参考这个[视频教程](http://pan.baidu.com/s/1qXeJhTE)。
安装完成之后，再去BIOS改回第一启动为硬盘。第一次进入CentOS系统，第一件事就是联网！！关于网络配置[请参考](http://jingyan.baidu.com/article/fc07f9891d186512ffe51935.html)。网络连通之后，然后以root身份进入终端Terminal，输入一下命令更新系统内核软件：

    yum -y update
如果yum源不是国内镜像，可能速度比较慢，建议使用国内yum源镜像站点，[请参考](http://inslow.com/yum-mirrors/)。
### 第②步Tomcat的安装与配置
安装Tomcat命令：

    yum -y install tomcat6 tomcat6-webapps tomcat6-admin-webapps tomcat6-docs-webapp tomcat6-javadoc
然后启动Tomcat服务：

    service tomcat6 start 
访问http://localhost:8080/如果出现不了以下网页，说明是防火墙策略问题，[请参考](http://inslow.com/iptables)。
![tomcat](http://ww2.sinaimg.cn/mw690/9325ea4dgw1f05f4n79wvj20dw06t74s.jpg)
### 第③步MySQL的安装与配置
安装MySQL命令：

    yum -y install mysql mysql-server mysql-devel
启动MySQL服务：

    /etc/init.d/mysqld start
设置MySQL服务为开机自启动：

    chkconfig mysqld on
为MySQL root账户设置密码：

    mysqladmin -u root password '你想要设置的密码'
这时我们就可以通过以下命令登录MySQL数据库了：

    mysql -uroot -p
最后重启MySQL：

    /etc/init.d/mysqld restart
### 第④步JDK的安装与配置
安装JDK命令：

    yum -y install java-1.7.0-openjdk  java-1.7.0-openjdk-devel
直到最后一行出现Complete!表示JDK安装完成。
然后使用命令查看Java默认安装目录：

    whereis java
找到目录之后开始配置Java环境变量（这里采用全局设置方法，就是修改etc/profile，它是是所有用户的共用的环境变量）：

    vi /etc/profile
然后在末尾添加：

    export JAVA_HOME=/usr/lib/jvm/java-1.7.0-openjdk-1.7.0.91.x86_64
    export JRE_HOME=/usr/lib/jvm/java-1.7.0-openjdk-1.7.0.91.x86_64/jre
    export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar:$JRE_HOME/lib:$CLASSPATH
    export PATH=$JAVA_HOME/bin: $PATH
然后保存。最后要使profile生效：

    source /etc/profile
在终端输入：
 
    Java -version
出现以下信息就证明JDK安装成功了。

    java version "1.7.0_91"
    OpenJDK Runtime Environment (rhel-2.6.2.2.el6_7-x86_64 u91-b00)
    OpenJDK 64-Bit Server VM (build 24.91-b01, mixed mode)