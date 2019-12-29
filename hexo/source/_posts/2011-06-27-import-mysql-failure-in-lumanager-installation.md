---
id: 138
title: LuManager安装过程导入Mysql失败的解决办法
date: 2011-06-27T15:12:14+00:00
author: admin
layout: post
guid: http://www.shootsoft.net/?p=138
categories:
  - Linux
tags:
  - LuManager
  - MySQL安装失败
  - 解决办法
---
[LuManager](http://www.zijidelu.org/)是一个优秀的国产Linux服务器管理软件，集成了Apache，Nigix，MySQL，FTP，Bind，Memcache，PHP5等软件包，可以实现Apache与Nigix的一键切换，多服务器负载均衡，域名智能解析，用户管理，流量监测功能等。可以通过Web界面来管理整个服务器，还能一键安装DedeCMS，Discuz!等Web应用程序。

LuManager在安装和使用过程中可能碰到导入Mysql失败的情况。

一般有2种情况：

情况1 安装MySQL时出错

> Mysql 安装成功，继续安装LuNamp1.0
> 
> Mysql was successfully installed! Continue&#8230;
> 
> 已耗时：30 分钟
> 
> Runtime: 30 分钟
> 
> ERROR 2002 (HY000): Can&#8217;t connect to local MySQL server through socket &#8216;/tmp/mysql.sock&#8217; (2)
> 
> MySQL数据导入不成功，可能是数据库没启动，或者是MySQL没安装成功，请重装一次试试！
> 
> Mysql data was not imported！
> 
> LuNamp安装失败
> 
> LuNamp was install failed

分析：

原来系统安装了一个MySQL，在系统原有MySQL没有停止服务的时候开始安装了LuManager，有可能是原有MySQL服务产生了影响。

解决：

杀死系统中正在运行的MySQL

方法1

如果你知道原有的MySQL服务器root用户密码，那么通过这个命令就能停止（忘记密码的看方法2）：

> mysqladmin -uroot -p&#8217;password&#8217; shutdown

注意：

1. /etc/init.d/mysql stop 并不是正确的停止mysql服务的方法！

2. 如果你试图通过 /usr/local/LuNamp/cmd 目录下的 mysql-stop 来停止服务，那么你可能会碰到如下提示：

> protest1:/usr/local/LuNamp/cmd# ./mysql-stop
> 
> 1
> 
> MySQL manager or server PID file could not be found! failed!

可以通过方法2来解决

方法2

首先确保当前是root用户，运行如下命令：

> protest1:/usr/local/LuNamp/cmd# ps -Af | grep mysqld

返回结果如下（注意加粗的那一行，那个PID就是MySQL的进程ID）：

> root      6928     1  0 Jun21 ?        00:00:00 /bin/sh /usr/bin/mysqld_safe
> 
> **mysql    17427  6928  0 14:56 ?        00:00:00 /usr/sbin/mysqld &#8211;basedir=/usr &#8211;datadir=/var/lib/mysql &#8211;user=mysql &#8211;pid-file=/var/run/mysqld/mysqld.pid &#8211;skip-external-locking &#8211;port=3306 &#8211;socket=/var/run/mysqld/mysqld.sock**
> 
> root     17428  6928  0 14:56 ?        00:00:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
> 
> root     17460 17340  0 14:58 pts/2    00:00:00 grep mysqld

接着运行

> protest1:/usr/local/LuNamp/cmd#Kill 17427

杀死了MySQL进程后，重新运行./zijidelu_install.sh就可以了

情况2 进入系统时出错，提示：

> <p lang="en-US">
>   Can&#8217;t connect to local MySQL server through socket &#8216;/tmp/mysql.sock'(2)
> </p>

截图：

<p style="text-align: center;">
  <a href="http://www.shootsoft.net/wp-content/uploads/2011/06/5876921168_e9950bddfc.jpg"><img class="aligncenter size-full wp-image-141" title="LuManager登录MySQL错误" src="http://www.shootsoft.net/wp-content/uploads/2011/06/5876921168_e9950bddfc.jpg" alt="" width="500" height="194" srcset="https://www.shootsoft.net/wp-content/uploads/2011/06/5876921168_e9950bddfc.jpg 500w, https://www.shootsoft.net/wp-content/uploads/2011/06/5876921168_e9950bddfc-300x116.jpg 300w" sizes="(max-width: 500px) 100vw, 500px" /></a>
</p>

解决方法：

首先参考情况1的方法1或者方法2来杀死当前正在运行的MySQL服务，然后以root用户身份进入

> /usr/local/LuNamp/cmd

运行当前目录的mysql-start

> protest1:/usr/local/LuNamp/cmd#./mysql-start

然后刷新LuManager的Web界面应该就能顺利进入了:-)

&nbsp;