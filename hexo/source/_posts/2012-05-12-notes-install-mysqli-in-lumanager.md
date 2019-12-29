---
id: 174
title: LuManager单独安装mysqli手记
date: 2012-05-12T14:59:31+00:00
author: admin
layout: post
guid: http://www.shootsoft.net/?p=174
categories:
  - Linux
tags:
  - LuManager
  - mysqli
  - mysqli源码
  - 单独安装mysqli
---
在开始之前，首先试一下这个这个帖子里提到的方法

<http://www.zijidelu.org/forum.php?mod=viewthread&tid=46214>

如果不行，按照下面的方法进行(不仅仅适用于LuManager，如果是自己编译安装的php也可以这么做)：

首先确定你正在使用的php版本以及php.ini的位置，LuManager自带了几个版本。如果是默认安装，应该是5.2.17。php.ini的位置应该是在

/usr/local/php_fcgi/lib/php.ini

要确定这些信息，可以自己编写一个 info.php

>  <?php
> 
> phpinfo();
> 
> ?>

把文件存放到网站根目录，然后浏览一下。

比如 <http://yourdomain.com/info.php>

到上述帖子里提到的LuManager的安装源码包里，我的解压到了/root/zijidelu_install路径下

进入LuNamp的soft路径

> cd /root/zijidelu_install/LuNamp/soft

用ls查看一下，应该有这个文件

> ls php-5.2.17.tar.gz

解压缩

> tar -zxvf php-5.2.17.tar.gz

进入mysqli的安装路径

> cd php-5.2.17/ext/mysqli

这里是mysqli的源码，编译之前我们还需要借助phpize这个工具（感谢<a title="一只猪的微博" href="http://t.qq.com/mohock" target="_blank">@一只猪</a>同学的帮助:-)），它存在于你的php安装路径，比如

> /usr/local/php_fcgi/bin/phpize

在当前路径下运行一下，看到如下提示：

> Configuring for:
> 
> PHP Api Version:         20041225
> 
> Zend Module Api No:      20060613
> 
> Zend Extension Api No:   220060519
> 
> configure.in:3: warning: prefer named diversions
> 
> configure.in:3: warning: prefer named diversions

继续运行下面这几个命令

>  ./configure -with-php-config=/usr/local/php\_fcgi/bin/php-config -with-mysqli=/usr/local/mysql/bin/mysql\_config
> 
> make
> 
> make install

最后会看到这个提示：

> Installing shared extensions:     /usr/local/php_fcgi/lib/php/extensions/no-debug-non-zts-20060613/

说明安装成功。

从LuManager后台重启一下ngix（如果你只用Apache那就重启一下Apache）

再刷新一下info.php，搜索mysqli，如果还搜不到就得自己编辑一下php.ini了

编辑之前double check一下mysqli.so是不是已经安装到上述路径了

> cd  /usr/local/php_fcgi/lib/php/extensions/no-debug-non-zts-20060613/
> 
> ls

如果看到mysqli.so就继续

> vim /usr/local/php_fcgi/lib/php.ini

输入

> /mysqli

然后回车，定位到这一行

> ;extension=php_mysqli.dll

输入i，进入编辑模式，然后在这之前或者之后加入一行

> extension=mysqli.so

按下ESC，然后输入

> :wq

如果对vim编辑不熟悉可以从LuManager后台在线编辑php.ini

保存之后重启一下ngix

再次查看info.php

<h2 style="text-align: center; line-height: normal; widows: 2; text-transform: none; background-color: #ffffff; font-variant: normal; font-style: normal; text-indent: 0px; letter-spacing: normal; font-family: sans-serif; white-space: normal; orphans: 2; color: #000000; font-size: 20px; word-spacing: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px;">
  <a name="module_mysqli"></a>mysqli
</h2>

&nbsp;

<table class="ke-zeroborder" style="text-align: left; widows: 2; text-transform: none; background-color: #ffffff; text-indent: 0px; letter-spacing: normal; border-collapse: collapse; font: medium sans-serif; white-space: normal; orphans: 2; color: #000000; margin-left: auto; margin-right: auto; word-spacing: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px;" width="600" border="0" cellpadding="3">
  <tr class="h" style="background-color: #9999cc; color: #000000; font-weight: bold;">
    <th style="text-align: center !important; font-family: sans-serif; font-size: 12px; vertical-align: baseline; border-image: initial; border: #000000 1px solid;">
      MysqlI Support
    </th>
    
    <th style="text-align: center !important; font-family: sans-serif; font-size: 12px; vertical-align: baseline; border-image: initial; border: #000000 1px solid;">
      enabled
    </th>
  </tr>
  
  <tr>
    <td class="e" style="background-color: #ccccff; font-family: sans-serif; color: #000000; font-size: 12px; vertical-align: baseline; font-weight: bold; border-image: initial; border: #000000 1px solid;">
      Client API library version
    </td>
    
    <td class="v" style="background-color: #cccccc; font-family: sans-serif; color: #000000; font-size: 12px; vertical-align: baseline; border-image: initial; border: #000000 1px solid;">
      5.1.56
    </td>
  </tr>
  
  <tr>
    <td class="e" style="background-color: #ccccff; font-family: sans-serif; color: #000000; font-size: 12px; vertical-align: baseline; font-weight: bold; border-image: initial; border: #000000 1px solid;">
      Client API header version
    </td>
    
    <td class="v" style="background-color: #cccccc; font-family: sans-serif; color: #000000; font-size: 12px; vertical-align: baseline; border-image: initial; border: #000000 1px solid;">
      5.1.56
    </td>
  </tr>
  
  <tr>
    <td class="e" style="background-color: #ccccff; font-family: sans-serif; color: #000000; font-size: 12px; vertical-align: baseline; font-weight: bold; border-image: initial; border: #000000 1px solid;">
      MYSQLI_SOCKET
    </td>
    
    <td class="v" style="background-color: #cccccc; font-family: sans-serif; color: #000000; font-size: 12px; vertical-align: baseline; border-image: initial; border: #000000 1px solid;">
      /tmp/mysql.sock
    </td>
  </tr>
</table>

&nbsp;

&nbsp;