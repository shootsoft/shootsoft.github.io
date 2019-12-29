---
id: 149
title: SAE Storage批量上传工具使用教程
date: 2012-03-28T17:18:58+00:00
author: admin
layout: post
guid: http://www.shootsoft.net/?p=149
image: /wp-content/uploads/2012/03/poweredby.png
categories:
  - Documents
tags:
  - SAE
  - Sina App Engine
  - Storage
  - 批量上传
  - 教程
---
0.1 版本下载：

<a href="https://github.com/downloads/shootsoft/SAEMutipleUploads/SAE%20Mutiple%20Uploads%200.1.7z" data-ke-src="https://github.com/downloads/shootsoft/SAEMutipleUploads/SAE%20Mutiple%20Uploads%200.1.7z">https://github.com/downloads/shootsoft/SAEMutipleUploads/SAE%20Mutiple%20Uploads%200.1.7z</a>

源码下载：

<a href="https://github.com/shootsoft/SAEMutipleUploads" data-ke-src="https://github.com/shootsoft/SAEMutipleUploads">https://github.com/shootsoft/SAEMutipleUploads</a>

首先在本地编辑【SAE\_PHP】目录下的【sae\_mutiple_uploads.php】文件，重新设置密码。

在SAE上创建好自己的应用，如果你是从应用仓库安装的Wordpress，可以跳过这一步直接去上传PHP文件了；否则需要自己创建Storage服务的domain：

[<img class="aligncenter size-full wp-image-152" title="Storage Domain" src="http://www.shootsoft.net/wp-content/uploads/2012/03/Storage-Domain2.png" alt="" width="319" height="183" srcset="https://www.shootsoft.net/wp-content/uploads/2012/03/Storage-Domain2.png 319w, https://www.shootsoft.net/wp-content/uploads/2012/03/Storage-Domain2-300x172.png 300w" sizes="(max-width: 319px) 100vw, 319px" />](http://www.shootsoft.net/wp-content/uploads/2012/03/Storage-Domain2.png)

上传有很多种方法，可以使用SAE的发布工具，也可以使用SVN，这里介绍从网页上传的方法。

从【我的首页】进入应用程序的配置界面，选择代码管理：

<p style="text-align: center;">
  <a href="http://www.shootsoft.net/wp-content/uploads/2012/03/代码管理.png"><img class="aligncenter  wp-image-153" title="代码管理" src="http://www.shootsoft.net/wp-content/uploads/2012/03/代码管理.png" alt="" width="481" height="386" srcset="https://www.shootsoft.net/wp-content/uploads/2012/03/代码管理.png 534w, https://www.shootsoft.net/wp-content/uploads/2012/03/代码管理-300x241.png 300w" sizes="(max-width: 481px) 100vw, 481px" /></a>
</p>

从右边选择编辑代码，需要安全码验证：

<p style="text-align: center;">
  <a href="http://www.shootsoft.net/wp-content/uploads/2012/03/编辑代码.png"><img class="aligncenter  wp-image-154" title="编辑代码" src="http://www.shootsoft.net/wp-content/uploads/2012/03/编辑代码.png" alt="" width="489" height="57" srcset="https://www.shootsoft.net/wp-content/uploads/2012/03/编辑代码.png 815w, https://www.shootsoft.net/wp-content/uploads/2012/03/编辑代码-300x34.png 300w" sizes="(max-width: 489px) 100vw, 489px" /></a>
</p>

在新打开的页面中，直接选择【上传文件】一个黄色的向上的箭头，选择【SAE\_PHP】目录下的【sae\_mutiple_uploads.php】。

[<img class="aligncenter size-full wp-image-155" title="上传文件" src="http://www.shootsoft.net/wp-content/uploads/2012/03/上传文件.png" alt="" width="268" height="120" />](http://www.shootsoft.net/wp-content/uploads/2012/03/上传文件.png)

打开【SAE Mutiple Uploads.exe】

<p style="text-align: center;">
  <a href="http://www.shootsoft.net/wp-content/uploads/2012/03/SAEMutipleUploads.png"><img class="aligncenter  wp-image-169" title="SAEMutipleUploads" src="http://www.shootsoft.net/wp-content/uploads/2012/03/SAEMutipleUploads.png" alt="" width="540" height="251" srcset="https://www.shootsoft.net/wp-content/uploads/2012/03/SAEMutipleUploads.png 600w, https://www.shootsoft.net/wp-content/uploads/2012/03/SAEMutipleUploads-300x139.png 300w" sizes="(max-width: 540px) 100vw, 540px" /></a>
</p>

【上传文件接收地址】指的就是刚才上传的php，假如你上传到了根目录，你的应用程序叫 testapp，那么这里就应该填

<a href="http://testapp.sinaapp.com/sae_upload_ramdom.php" data-ke-src="http://testapp.sinaapp.com/sae_upload_ramdom.php">http://testapp.sinaapp.com/sae_mutiple_uploads.php</a>

【命名空间】指Storage的Domain名称。

【密码】是第一步配置的密码

【本地路径】指要批量上传的本地文件夹路径，支持多级文件夹，上传过程会自己处理。

配置好后点击【上传】，等待完成即可。

**最后不要忘记了删除那个批量上传文件的sae\_mutiple\_uploads.php。**

&nbsp;

&nbsp;