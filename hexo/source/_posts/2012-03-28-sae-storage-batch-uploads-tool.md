---
id: 162
title: '发布SAE Storage批量上传工具[开源]'
date: 2012-03-28T17:25:04+00:00
author: admin
layout: post
guid: http://www.shootsoft.net/?p=162
image: /wp-content/uploads/2012/03/poweredby.png
categories:
  - News
tags:
  - SAE Storage
  - 批量上传
---
最近云计算如火如荼，于是也忍不住去尝了尝鲜。SAE（Sina App Engine）是新浪推出的云计算平台，直接用微博账号就能登录，绑定手机号以后就可以开始使用了，支持PHP/Java/Python。一个比较有特色的是应用程序商店，逛了一圈发现有Wordpress，于是动起了把本站迁移到SAE的念头。上网搜了一圈，发现这篇教程倒是很详细：

> <a href="http://www.mobai.org/2011/09/30/wp2sae/" data-ke-src="http://www.mobai.org/2011/09/30/wp2sae/">http://www.mobai.org/2011/09/30/wp2sae/</a>

但是第一个评论就击退了念头：

> 看来wordpress的转入，确实很麻烦。尤其是图片的部分，5年，每年12个月，就要手动创建60的路径，然后每个路径再上传图片，这是很可怕的工作量了。。。唉。

难道没有好的办法了么？摸索了一番之后决定自己开发一个SAE Storage的批量上传工具。

原理很简单，搭建Wordpress之后，再通过SVN或者手动上传一个额外的PHP，这个PHP专门用于接收上传的文件，然后转存到Storage。路径与本地的或者原有路径保持一致即可。本地上传使用C#开发。源码托管在Github上：[https://github.com/shootsoft/SAEMutipleUploads](https://github.com/shootsoft/SAEMutipleUploads "SAE Mutiple Upload")

<p style="text-align: center;">
  <a href="http://www.shootsoft.net/wp-content/uploads/2012/03/SAE.png"><img class="aligncenter  wp-image-156" title="SAE" src="http://www.shootsoft.net/wp-content/uploads/2012/03/SAE.png" alt="" width="483" height="174" srcset="https://www.shootsoft.net/wp-content/uploads/2012/03/SAE.png 604w, https://www.shootsoft.net/wp-content/uploads/2012/03/SAE-300x108.png 300w" sizes="(max-width: 483px) 100vw, 483px" /></a>
</p>

[SAE Storage批量上传工具的使用教程参考这里](http://www.shootsoft.net/149/ "SAE Storage 批量上传工具教程")。