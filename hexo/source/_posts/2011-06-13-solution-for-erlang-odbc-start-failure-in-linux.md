---
id: 127
title: Linux下Erlang中无法运行odbc:start()的解决办法
date: 2011-06-13T09:51:28+00:00
author: admin
layout: post
guid: http://www.shootsoft.net/?p=127
categories:
  - Erlang
tags:
  - Erlang
  - Linux
  - odbc:start()
  - unixodbc-dev
---
之前碰到过一次，但是当时是和ssl的问题一起解决的，所以再一次的疏忽了，Erlang安装的时候一定要确认所有需要的库都正确安装了。

错误情况是在erl环境中运行 odbc:start(). 的时候

抛出如下的异常：

> ** exception error: undefined function odbc:start/0

该异常的解决办法和《[Erlang {&#8220;no such file or directory&#8221;,&#8221;crypto.app&#8221;}  的解决方法](http://www.shootsoft.net/123/ "Erlang {“no such file or directory”,”crypto.app”} 的解决方法")》类似首先确认linux下安装了如下的包：

> apt-get  install unixodbc unixodbc-dev

接着重新[安装erlang](http://www.shootsoft.net/129/ "安装Erlang")解决。

参考:《[Linux(Debian)下正确编译安装Erlang的方法](http://www.shootsoft.net/129/ "Linux(Debian)下正确编译安装Erlang的方法")》