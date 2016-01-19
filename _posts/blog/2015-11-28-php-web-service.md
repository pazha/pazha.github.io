---
layout: post
title: CentOS下LAMP环境搭建
category: blog
description: 关于Linux+Apache+MySQL+PHP的Web服务环境搭建
---

**起因：**LAMP架构一直是企业开发中最稳定的开发环境。

**版本选择（仅供参考）：**

    CentOS6.7(Linux操作系统)
    Apache2.2(Web服务器)
    MySQL5.1（数据库）
    PHP5.3（编程语言）
**安装方式：**yum在线安装

**安装顺序：**CentOS→Apache→MySQL→PHP
### 第①步CentOS的安装与配置
从CentOS官网（www.centos.org）下载CentOS6.7DVD的ISO镜像文件。为了方便起见，这里我从阿里云镜像网站下载：

    http://mirrors.aliyun.com/centos/6.7/isos/x86_64/CentOS-6.7-x86_64-bin-DVD1.iso
下载完成之后，使用电脑店（u.diannaodian.com）或者老毛桃(www.laomaotao.org)把镜像刻录到U盘中，不会的请自行百度。刻录完成之后，进入主板BIOS设置U盘为第一启动。然后插入U盘，出现下面这个画面选择第一项便可以开始安装CentOS6.7了。![CentOS6.7](http://ww3.sinaimg.cn/mw690/9325ea4dgw1f03y4kucocj20fe080q5g.jpg)

图形化安装界面比较简单，具体安装步骤请自行百度或者参考这个[视频教程](http://pan.baidu.com/s/1qXeJhTE)。
安装完成之后，再去BIOS改回第一启动为硬盘。第一次进入CentOS系统，第一件事就是联网！！关于网络配置[请参考](http://jingyan.baidu.com/article/fc07f9891d186512ffe51935.html)。网络连通之后，然后以root身份进入终端Terminal，输入一下命令更新系统内核软件：

    yum -y update
如果yum源不是国内镜像，可能速度比较慢，建议使用国内yum源镜像站点，[请参考](http://inslow.com/yum-mirrors/)。
### 第②步Apache的安装与配置
安装Apache命令：

    yum -y install httpd
然后启动Apache服务：

    /etc/init.d/httpd start 
这时候Apache启动之后会提示错误：

    正在启动 httpd:httpd: Could not reliably determine the server's fully qualif domain name, using ::1 for ServerName 
需要配置httpd.conf文件：

    vi /etc/httpd/conf/httpd.conf 
找到#ServerName localhost:80，去掉“#”，即改为ServerName localhost:80。然后:wq!保存退出。
设置Apache服务为开机自启动：

    chkconfig httpd on
然后重启Apache服务：
   
    /etc/init.d/httpd restart
如果此时还是测试不通，说明是防火墙策略问题，[请参考](http://inslow.com/iptables/)。
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
### 第④步PHP的安装与配置
安装PHP及其组件命令：

    yum -y install php php-mysql php-common php-mbstring php-gd php-imap php-ldap php-odbc php-pear php-xml php-xmlrpc
然后重启MySQL和Apache：

    service mysqld restart
    service httpd restart
最后就可以输入http://localhost或者127.0.0.1测试了。
![php5.3.3](http://ww1.sinaimg.cn/mw690/9325ea4dgw1f05e8fpkvgj20gi09uaav.jpg)