---
id: 108
title: .htaccess权限设置不正确导致无法Rewrite
date: 2011-01-28T07:02:23+00:00
author: admin
layout: post
guid: http://www.shootsoft.net/?p=108
categories:
  - Others
tags:
  - .htaccess文件权限
  - Rewrite
---
最近在配置一个php的网站程序时碰到了.htaccess文件权限设置不正确而导致Rewrite失效的情况。
  
起初将网站程序全部上传，运行正确，后来有一个地方读写权限碰到问题，于是鲁莽地将整个文件夹带循环方式的权限全部设置为 777
  
chmod -R 777 webroot
  
经过一番设置之后，网站运行OK了，就稍微考虑了一下SEO方面的问题，于是启用了伪静态，但是不知道为甚，伪静态不起作用，仔细检查了相关的正则表达式，完全OK，但是服务器上就是不起作用。

仔细分析了一下：同一个服务器上的另外一个程序Rewrite完全正确，表明Apache的Rewrite模块是工作正常的；后来比较这两个.htaccess的文件权限发现了情况。这个有问题的站点下的.htaccess文件权限是777，而另外一个是666。

上网查阅了一番：系统为了确保安全，对于.htaccess权限为 777 的情况下，可能会拒绝执行，于是去掉可执行属性，一切恢复正常。