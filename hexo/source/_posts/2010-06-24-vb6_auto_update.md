---
id: 56
title: VB6程序的自动更新模块
date: 2010-06-24T21:20:42+00:00
author: admin
layout: post
guid: http://www.shootsoft.net/?p=56
sidebar_layout:
  - ""
the_sidebar:
  - ""
lower_sidebar:
  - ""
content_sidebar:
  - ""
colorscheme:
  - ""
full_width_widget:
  - ""
hide_bottom_sidebars:
  - ""
featureboxes:
  - ""
carousel_items:
  - ""
carousel_mode:
  - ""
carousel_ngen_gallery:
  - ""
featuretitle:
  - ""
featuretext:
  - ""
featuremedia:
  - ""
categories:
  - Download
---
这个是VB6编写程序时常常碰到的问题:想实现像瑞星那样自动连接到网络下载更新程序,然后再在本地实现更新的功能.这里会遇到三个问题:
  
1.是版本的控制.假如从1.1到1.2只更新了几个文件,1.2到1.3又更新了另外几个文件,假如用户错过了1.1版的更新,那么这个1.3版的升级包应该不仅适合于1.2,并且也应该适合1.1才行.但是假如1.2-1.3升级包特别小,而1.1-1.2升级包特别大的话那么1.2版升级的用户就不需要下载非常大的升级包才行.以后的每个版本升级都要照顾到1.1版的升级才行.所以,简单的办法是对需要有可能升级的所有文件进行版本控制.每个文件对应一个版本号.当某个文件版本号低于服务器上文件的版本号时就进行升级的操作.
  
2.是更新程序自身的更新.像瑞星之类的软件都能实现对更新程序自身的更新.而对正在运行的一个exe文件进行读写在VB6里是不太容易实现的.这里可以采取&#8221;曲线救国&#8221;的道路:程序一运行先将自身拷贝一份并改名为temp.exe.然后运行这个temp.exe来进行连接服务器下载更新文件的操作.
  
3.是目录的检测.假如更新文件放在新建的文件夹里那么程序应当可以新建文件夹(多级).我是从www.planet-source-code.com找到的一个创建多级目录的函数:-)
  
其他还有一些比如:检测正在运行的主程序,关闭主程序等操作直接调用相应的API即可实现.
  
本模块升级服务器采用的是FTP,可以用进度条来显示下载文件个数和单个文件下载进度.

[<img class="alignnone size-full wp-image-57" title="VB6 Auto Update" src="http://www.shootsoft.net/wp-content/uploads/2010/06/06012614252436.gif" alt="" width="479" height="351" srcset="https://www.shootsoft.net/wp-content/uploads/2010/06/06012614252436.gif 479w, https://www.shootsoft.net/wp-content/uploads/2010/06/06012614252436-300x219.gif 300w" sizes="(max-width: 479px) 100vw, 479px" />](http://www.shootsoft.net/wp-content/uploads/2010/06/06012614252436.gif)

<a href="http://code.google.com/p/shootsoft/downloads/detail?name=VB6_Auto_Update.rar" target="_blank">猛击这里下载</a>