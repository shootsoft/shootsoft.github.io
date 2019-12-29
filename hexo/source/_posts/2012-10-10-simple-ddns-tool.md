---
id: 178
title: '[C#开源]基于DNSPod的动态域名解析工具SimpleDDns'
date: 2012-10-10T13:59:02+00:00
author: admin
layout: post
guid: http://www.shootsoft.net/?p=178
categories:
  - Download
tags:
  - 'C#'
  - DNSPod
  - 域名动态解析
  - 开源
---
今天碰到一个比较小众的需求：动态解析一个二级域名到内网IP上。域名本身是托管在DNSPod上的，先试了试官方提供的客户端，发现只能解析到外网IP，由于公司内部是一个局域网，出口的外网IP都是一样的，所以意义不大。好在DNSPod的API非常齐全，参考：<https://www.dnspod.cn/Support/Api>。

仔细研究了之后决定自己写一个。

配置文件选用JSON格式，最近做了不少项目，配置文件基本都是JSON。JSON格式的配置文件无论程序还是人为读取，可读性都非常好。C#下有很多JSON的类库，由于之前多次使用FastJSON，所以继续使用：[http://www.codeproject.com/Articles/159450/fastJSON](http://www.codeproject.com/Articles/159450/fastJSON "FastJSON")

但是不得不吐槽一下DNSPod的API格式：比如Record类型的id属性，一会儿是数字类型，一会儿又是字符串类型，实在是有些不方便，特别是碰上FastJson这样愣头愣脑类型的解析器：为了追求速度，对JSON格式做了非常严格的规定，数字就是数字，要么你去修改类型，要么修改FastJson的代码用int.trypase去尝试一下。JSON.NET目前还是.NET平台下最好的JSON解析，只是用在这个项目里觉得体积还是有些大了。

DNSPod的API都是标准的REST请求，返回XML或者JSON。迅速完成核心需求：

> 动态解析域名到内网IP上

传送门：<https://github.com/shootsoft/SimpleDDns>

&nbsp;