---
id: 137
title: WinSCP跨Linux（多Linux台机器之间）拷贝传输文件
date: 2011-06-16T17:24:20+00:00
author: admin
layout: post
guid: http://www.shootsoft.net/137/
categories:
  - Linux
tags:
  - Linux拷贝文件
  - WinSCP
  - 多台
---
&nbsp;

<p style="margin:0in;font-size:11.0pt">
  <span lang="zh-CN" style="font-family:宋体">这纯属一个使用技巧，找了很多</span><span lang="en-US" style="font-family:Calibri">Linux</span><span lang="zh-CN" style="font-family:宋体">的</span><span lang="en-US" style="font-family:Calibri">Windows</span><span lang="zh-CN" style="font-family:宋体">客户端，貌似都不能在同一个用户界面上跨机器拷贝传输文件，用来用去还是</span><span lang="en-US" style="font-family:Calibri">WinSCP</span><span lang="zh-CN" style="font-family:宋体">顺手，以前跨机器传输的时候都是开多个窗口，拖放。今天偶然发现</span><span lang="en-US" style="font-family:Calibri">WinSCP</span><span lang="zh-CN" style="font-family:宋体">也可以在同一个用户界面上跨机器拷贝传输文件。</span>
</p>

<p style="margin:0in;font-family:宋体;font-size:11.0pt">
  &nbsp;
</p>

<p style="margin:0in;font-size:11.0pt">
  <span lang="zh-CN" style="font-family:宋体">首先要确保</span><span lang="en-US" style="font-family:Calibri">WinSCP</span><span lang="zh-CN" style="font-family:宋体">的工具栏&ldquo;会话按钮&rdquo;是显示状态，方便在多台</span><span lang="en-US" style="font-family:Calibri">Linux</span><span lang="zh-CN" style="font-family:宋体">之间切换界面</span>
</p>

<p style="margin:0in;font-family:宋体;font-size:11.0pt">
  <a href="http://www.flickr.com/photos/63244076@N04/5839525910/" title="Flickr 上 model123 的 WinSCP会话按钮"><img alt="WinSCP会话按钮" height="458" src="http://farm4.static.flickr.com/3491/5839525910_bc8be23141.jpg" width="443" /></a>
</p>

<p style="margin:0in;font-size:11.0pt">
  <span lang="zh-CN" style="font-family:宋体">点击&ldquo;会话按钮&rdquo;工具栏的倒数第二个按钮，可以登录更多的</span><span lang="en-US" style="font-family:Calibri">Linux</span><span lang="zh-CN" style="font-family:宋体">机器（注意：要拷贝的文件的目标机器必须先在这里登录）</span>
</p>

<p style="margin:0in;font-family:宋体;font-size:11.0pt">
  <img alt="WinSCP打开更多会话" height="144" src="http://farm4.static.flickr.com/3134/5838974697_f95f92bdb3.jpg" width="280" />
</p>

<p style="margin:0in;font-family:宋体;font-size:11.0pt">
  在某一台需要拷贝的文件上单击鼠标右键，选择&ldquo;远程复制&rdquo;
</p>

<p style="margin:0in;font-family:宋体;font-size:11.0pt">
  <a href="http://www.flickr.com/photos/63244076@N04/5838974729/" title="Flickr 上 model123 的 WinSCP远程复制菜单"><img src="http://farm3.static.flickr.com/2727/5838974729_3996144034.jpg" width="329" height="267" alt="WinSCP远程复制菜单" /></a>
</p>

<p style="margin:0in;font-size:11.0pt">
  <span lang="zh-CN" style="font-family:宋体">在新弹出的窗口中&ldquo;目标会话&rdquo;就可以选择其他的</span><span lang="en-US" style="font-family:Calibri">Linux</span><span lang="zh-CN" style="font-family:宋体">机器以及对应的目录了。</span>
</p>

<p style="margin:0in;font-family:宋体;font-size:11.0pt">
  <a href="http://www.flickr.com/photos/63244076@N04/5838974749/" title="Flickr 上 model123 的 WinSCP远程复制对话框"><img src="http://farm6.static.flickr.com/5119/5838974749_9f412d125a.jpg" width="336" height="211" alt="WinSCP远程复制对话框" /></a>
</p>

<p style="margin:0in;font-family:宋体;font-size:11.0pt">
  缺点就是不能同时拷贝到多台机器，以及文件拷贝实际上是先拷贝到本地，再拷贝到远程
</p>