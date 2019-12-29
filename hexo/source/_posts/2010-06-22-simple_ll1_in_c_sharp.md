---
id: 27
title: 'LL(1)文法判定[C#代码下载]'
date: 2010-06-22T22:20:28+00:00
author: admin
layout: post
guid: http://shootsoft.org/blog/?p=27
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
这个是大二时候的编译原理课程设计作业。用C#实现。参考书籍：《编译原理》 张素琴 吕映之 蒋维杜 戴桂兰 著 清华大学出版社 2005年2月 第2版。

先后计算First集，Follow集和Sellect集，然后判断是否是LL(1)文法，最后判断句子。**<span style="color: #ff0000;">生成结果界面很Cool</span>**。

**运行时注意先加载或编辑符号集，然后加载或编辑产生式集，最后才输入测试句子进行测试。**

[<img class="alignnone size-full wp-image-28" title="LL1" src="http://www.shootsoft.net/wp-content/uploads/2010/06/image007.gif" alt="" width="474" height="1178" srcset="https://www.shootsoft.net/wp-content/uploads/2010/06/image007.gif 474w, https://www.shootsoft.net/wp-content/uploads/2010/06/image007-412x1024.gif 412w" sizes="(max-width: 474px) 100vw, 474px" />](http://www.shootsoft.net/wp-content/uploads/2010/06/image007.gif)

SimpleLL1目录下为源程序
  
EXE目录下为编译好的可执行文件
  
Product1.txt~Product4.txt为测试用产生式（可直接在程序中加载）
  
Symbols.txt为测试用符号集（可直接在程序中加载）

转载或引用请注明出处:www.shootsoft.net

<a href="http://code.google.com/p/shootsoft/downloads/detail?name=ll1.rar" target="_blank">猛击这里下载</a>