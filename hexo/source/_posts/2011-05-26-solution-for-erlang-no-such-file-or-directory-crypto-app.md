---
id: 123
title: 'Erlang {&#8220;no such file or directory&#8221;,&#8221;crypto.app&#8221;}  的解决方法'
date: 2011-05-26T16:39:33+00:00
author: admin
layout: post
guid: http://www.shootsoft.net/123/
categories:
  - Erlang
tags:
  - crypto.app
  - Erlang
  - OpenSSL
  - ssl
  - 解决
---
&nbsp;

<p style="margin:0in;font-size:11.0pt">
  <span lang="zh-CN" style="font-family:宋体">一台新安装的</span><span lang="en-US" style="font-family:Calibri">Debian Linux 6.0, </span><span lang="zh-CN" style="font-family:宋体">安装了</span><span lang="en-US" style="font-family:Calibri">Erlang R14B02</span><span lang="en-US" style="font-family:宋体">. </span><span lang="zh-CN" style="font-family:宋体">直接运行</span><span lang="en-US" style="font-family:宋体">erl</span><span lang="zh-CN" style="font-family:宋体">，输入一些测试，没有问题。但是部署一个</span><span lang="en-US" style="font-family:宋体">Erlang</span><span lang="zh-CN" style="font-family:宋体">的应用程序之后，启动出错，主要提示为：</span>
</p>

<p style="margin:0in;font-family:宋体;font-size:11.0pt">
  &nbsp;
</p>

<p lang="en-US" style="margin:0in;font-family:Calibri;font-size:17.0pt;color:#222222">
  {"no such file or directory","crypto.app"}
</p>

<p style="margin:0in;font-family:宋体;font-size:11.0pt">
  &nbsp;
</p>

<p style="margin:0in;font-size:11.0pt">
  <span lang="zh-CN" style="font-family:宋体">这个</span><span lang="en-US" style="font-family:Calibri">Erlang</span><span lang="zh-CN" style="font-family:宋体">的应用程序用到了</span><span lang="en-US" style="font-family:Calibri">openssl</span><span lang="zh-CN" style="font-family:宋体">相关的类库，检查了一遍系统的类库，发现</span><span lang="en-US" style="font-family:Calibri"> openssl-dev</span><span lang="zh-CN" style="font-family:宋体">这个库没有安装，</span><span lang="en-US" style="font-family:Calibri">apt-get</span><span lang="zh-CN" style="font-family:宋体">安装后继续出错，搜索发现</span><span lang="en-US" style="font-family:宋体">erlang-ssl</span><span lang="zh-CN" style="font-family:宋体">这个库没有，</span><span lang="en-US" style="font-family:宋体">apt-get</span><span lang="zh-CN" style="font-family:宋体">安装后还是无效。</span>
</p>

<p style="margin:0in;font-family:宋体;font-size:11.0pt">
  最后发现一个成功解决的案例：
</p>

<p style="margin:0in;font-family:宋体;font-size:11.0pt">
  &nbsp;
</p>

<p style="margin:0in;font-family:Calibri;font-size:11.0pt">
  <a href="http://permalink.gmane.org/gmane.comp.networking.rabbitmq.general/5650">http://permalink.gmane.org/gmane.comp.networking.rabbitmq.general/5650</a>
</p>

<p style="margin:0in;font-family:Calibri;font-size:11.0pt">
  &nbsp;
</p>

<p style="margin:0in;font-size:11.0pt">
  <span lang="zh-CN" style="font-family:宋体">随后将</span><span lang="en-US" style="font-family:Calibri">Erlang</span><span lang="zh-CN" style="font-family:宋体">卸载，重新编译安装（加这个参数</span><span lang="zh-CN" style="font-family:palatino;color:#222222"> '&#8211;with-ssl=PATH'</span><span lang="zh-CN" style="font-family:宋体">）后一切正常。</span>
</p>

<p style="margin:0in;font-family:宋体;font-size:11.0pt">
  &nbsp;
</p>

<p style="margin:0in;font-size:11.0pt">
  <span lang="zh-CN" style="font-family:宋体">后记：</span><span lang="en-US" style="font-family:Calibri">Erlang</span><span lang="zh-CN" style="font-family:宋体">在编译的时候如果系统缺少一些类库，比如</span><span lang="en-US" style="font-family:Calibri">odbc,ssl</span><span lang="zh-CN" style="font-family:宋体">等，会给出一些警告信息，但是并不会阻塞后面的安装，安装成功后一般会认为安装成功了（基本的测试也能通过），但是实际上一些</span><span lang="en-US" style="font-family:Calibri">erlang</span><span lang="zh-CN" style="font-family:宋体">的类库并没有成功编译安装，这种情况下重新编译安装即可。</span>
</p>