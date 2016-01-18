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
从CentOS官网（www.centos.org）下载CentOS6.7DVD的ISO镜像文件。为了方便起见，这里我从阿里云镜像网站下载。地址为（大小5.63GB）：

    http://mirrors.aliyun.com/centos/6.7/isos/x86_64/CentOS-6.7-x86_64-bin-DVD1.iso
下载完成之后，使用电脑店（u.diannaodian.com）或者老毛桃(www.laomaotao.org)把镜像刻录到U盘中，不会的请自行百度。刻录完成之后，进入主板BIOS设置U盘为第一启动。然后插入U盘，出现下面这个画面选择第一项变可以开始安装CentOS6.7了。![CentOS6.7](http://ww3.sinaimg.cn/mw690/9325ea4dgw1f03y4kucocj20fe080q5g.jpg)
图形化安装界面比较简单，具体安装步骤请自行百度或者参考这个[视频教程](http://pan.baidu.com/s/1qXeJhTE)。
### 第②步Apache的安装与配置

