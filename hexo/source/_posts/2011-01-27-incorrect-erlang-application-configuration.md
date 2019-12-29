---
id: 102
title: Erlang应用程序配置不正确导致不正常启动的问题
date: 2011-01-27T15:29:59+00:00
author: admin
layout: post
guid: http://www.shootsoft.net/?p=102
categories:
  - Erlang
tags:
  - Erlang
  - 配置文件
---
在Erlang的应用程序配置文件 .app 配置不正确的时候，Erlang应用程序启动有可能出现表面上启动正常，但是实际上没有正确启动的问题。

如果程序没有问题，但是启动后就是无法访问，可以考虑仔细检查一遍 .app 的配置信息，看看是不是多了或者少了一个 {},[]或者,