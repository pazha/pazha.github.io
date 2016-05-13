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




CentOS6.5系统自带Open JDK1.7、1.6和1.5，但OpenJDK部分内容与SUN JDK不兼容，因此打算重新安装SUN JDK1.7来开发。

首先卸载系统自带的JDK:

1. 通过rpm命令查看Open JDK具体版本信息

    rpm -qa | grep java

结果可能为

    tzdata-java-2012c-1.el6.noarch
    java-1.7.0-openjdk-1.7.0.45-1.45.1.11.1.el6.x86_64

2. 通过rpm卸载JDK

    rpm -e --nodeps tzdata-java-2012c-1.el6.noarch
    rpm -e --nodeps java-1.7.0-openjdk-1.7.0.45-1.45.1.11.1.el6.x86_64

此时已经卸载了Open JDK了。

然后安装SUN公司JDK

1. 下载tag.gz文件(http://www.oracle.com/technetwork/java/javase/downloads/index.html)
2. 复制到 /opt目录 下并解压

    cp jdk-7u79-linux-x64.tar.gz /opt/
    tar -zxvf jdk-7u79-linux-x64.tar.gz

3. 配置全局环境变量
在 /etc/profile文件 内追加以下内容

# jdk7 settings
JAVA_HOME=/opt/jdk1.7.0_79
JRE_HOME=$JAVA_HOME/jre
PATH=$PATH:$JAVA_HOME/bin:$JRE_HOME/bin
CLASSPATH=:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar:$JRE_HOME/lib
export JAVA_HOME JRE_HOME PATH CLASSPATH

4.然后执行 source /etc/profile 使配置生效。
5. 在 /sbin目录 下建立java的软链接
此时我们在shell中输入java命令，将提示/usr/bin中找不到java命令，那是因为我们还没为$JAVA_HOME/bin/java在/sbin目录下建立软链接

ln -s /opt/jdk1.7.0_67/bin/java /sbin/java

最后查看Java版本，如果出现以下信息，说明安装成功

[root@localhost ~]# java -version
java version "1.7.0_80"
Java(TM) SE Runtime Environment (build 1.7.0_80-b15)
Java HotSpot(TM) 64-Bit Server VM (build 24.80-b11, mixed mode)

至此，所以安装完成。