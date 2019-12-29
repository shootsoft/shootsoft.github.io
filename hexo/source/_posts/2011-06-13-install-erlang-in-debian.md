---
id: 129
title: Linux(Debian)下正确编译安装Erlang的方法
date: 2011-06-13T09:46:57+00:00
author: admin
layout: post
guid: http://www.shootsoft.net/?p=129
categories:
  - Erlang
tags:
  - Debian
  - Erlang
  - Linux
  - 安装
---
因为几次都碰到安装后某些类库无法使用的问题，总结了一下：

> apt-get install gcc g++ build-essential m4 libncurses5-dev  libssl-dev  flex unixodbc-dev fop  libwxbase2.8-dev libwxgtk2.8-dev libgl1-mesa-dev libglu1-mesa-dev libglut3-dev libncurses5-dev  libc6  unixodbc  gcj openssl xsltproc

还有一个

> <p lang="en-US">
>   apt-get install sun-java6-jdk
> </p>

如果这个包不能正确安装，说明更新源可能有问题，用编辑器打开/etc/apt/sources.list增加一个

> deb http://http.us.debian.org/debian/ lenny main contrib non-free

然后保存关闭再次运行 apt-get update然后再安装，应该就没问题了。

库安装完成后在源码目录下

> ./configure &#8211;prefix=/usr/
  
> make
  
> make install

安装完成后输入erl就能使用最新的Erlang运行环境了

如果是直接apt-get install erlang的，就不用看这个了，我这个是erlang源码编译安装的说明。另外如果有错或者缺少某些类库，还请指出，谢谢。