---
id: 52
title: '计算机图形学算法演示程序[C#]'
date: 2010-06-24T21:12:04+00:00
author: admin
layout: post
guid: http://www.shootsoft.net/?p=52
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
演示了:
  
画直线的 DDA法,中点画线法,Bresenham算法
  
画圆的 中点画线法
  
多边形的 扫描线算法,区域填充扫描线算法
  
线段裁剪的 Cohen-Sutherland算法,中点分割算法,粱友栋-Barskey算法
  
Beizer曲线的 定义画法和递推画法

使用语言:C#
  
平台:.net 1.1
  
开发工具:Visual Studio .net 2003
  
大小:129KB
  
参考书籍:《计算机图形学基础教程》孙家广 胡事民 著 清华大学出版社

先配置方程,再画图
  
画线时可以不用多线程,若是选择了延时请务必把多线程也选上,多线程只适用演示区域填充扫描线算法时如果选择了延时,那么在把整个图形画出来时可能会碰到假死现象
  
Beizer曲线演示时需要把&#8221;辅助线&#8221;的&#8221;放大倍数&#8221;设小一点,当&#8221;放大倍数&#8221;小于5时,辅助线就不会被画到界面上了,这样才能看出曲线是否光滑
  
边界设置 如果没有需要不要修改,如果设置可以这样: 400,300 分别对应宽度,高度
  
原点设置 这个跟 边界设置 类似: 400,300 要是所演示图形一次屏幕没有显示完整,可以适当调整原点位置以显示完整

[<img src="http://www.shootsoft.net/wp-content/uploads/2010/06/graphics_show1.gif" alt="" title="graphics_show" width="530" height="471" class="alignnone size-full wp-image-53" srcset="https://www.shootsoft.net/wp-content/uploads/2010/06/graphics_show1.gif 530w, https://www.shootsoft.net/wp-content/uploads/2010/06/graphics_show1-300x266.gif 300w" sizes="(max-width: 530px) 100vw, 530px" />](http://www.shootsoft.net/wp-content/uploads/2010/06/graphics_show1.gif)

<a href="http://code.google.com/p/shootsoft/downloads/detail?name=GraphicsTestV1.rar" target="_blank" >猛击这里下载</a>