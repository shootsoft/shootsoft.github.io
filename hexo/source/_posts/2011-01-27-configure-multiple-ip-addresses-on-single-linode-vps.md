---
id: 98
title: 为Linode VPS配置多个IP及同一个VPS多个站点的配置（Debian版）
date: 2011-01-27T15:25:54+00:00
author: admin
layout: post
guid: http://www.shootsoft.net/?p=98
categories:
  - Documents
tags:
  - Apache
  - Debian
  - Linode
  - VPS
  - 多IP
  - 多站点
---
新年更新了一下空间，升级到了[Linode](http://www.linode.com/?r=9f0decd015b48a934934f3a59cee207d36de4c47)的VPS。这个群众都说好的VPS用起来是不错。可以选择以下的机房：
	  
• London, GB, UK
	  
• Newark, NJ, USA
	  
• Atlanta, GA, USA
	  
• Dallas, TX, USA
	  
• Fremont, CA, USA
  
参考：[http://www.linode.com/why.cfm](http://www.linode.com/?r=9f0decd015b48a934934f3a59cee207d36de4c47) ，我选的是Fremont

为了方便管理网站，我又额外购买了一个IP地址，貌似我的[Linode 512](http://www.linode.com/?r=9f0decd015b48a934934f3a59cee207d36de4c47)的配置只使用最多2个IP地址了。我对Debian比较熟悉，所以安装系统的时候毫不犹豫的选择了Debian，对Linux的不熟悉的还是不要选择Debian了，建议选择CentOS，参考一下网上的教程，安装Kloxo面板。

首先是购买多个IP地址，进入Linode的Dashboard界面，点击Extras，就能购买额外的IP地址了，由于Linode绑定了信用卡，所以会直接从信用卡上扣钱，每个额外IP地址的价格是$12一年，每个月是$1。如下图：
  
<img alt="" src="http://www.shootsoft.net/wp-content/uploads/2011/01/linode-extras.png" title="Linode Extras" class="alignnone" width="799" height="273" />

成功购买了IP地址之后，在Remote Access里可以看到所有的IP地址信息：
  
<img alt="" src="http://www.shootsoft.net/wp-content/uploads/2011/01/linode-remote-access.png" title="Linode Remote Access" class="alignnone" width="935" height="333" />

下面说重点：Debian的多个IP地址配置。首先看了一个《[为linode VPS配置多个IP教程](http://www.seamaple.net/2010/03/05/%E4%B8%BAlinode-vps%E9%85%8D%E7%BD%AE%E5%A4%9A%E4%B8%AAip%E6%95%99%E7%A8%8B%EF%BC%88%E5%8F%82%E8%80%83linode%E5%AE%98%E6%96%B9%E6%95%99%E7%A8%8B%EF%BC%89/)》，估计那个是CentOS的教程，Debian下IP地址配置文件是 /etc/network/interfaces 这个文件。用Putty登录Linode，用vim或者emacs打开(以emacs为例)：
  
emacs /etc/network/interfaces
  
默认的配置是通过DHCP自动获取的，内容如下：

> auto lo
  
> iface lo inet loopback
> 
> auto eth0
  
> iface eth0 inet dhcp

替换成

> auto lo
  
> iface lo inet loopback
> 
> auto eth0
  
> #iface eth0 inet dhcp
  
> iface eth0 inet static
  
> address 173.230.99.11
  
> netmask 255.255.255.0
  
> gateway 173.230.99.1
> 
> auto eth0:0
  
> iface eth0:0 inet static
  
> address 173.230.44.88
  
> netmask 255.255.255.0
  
> gateway 173.230.44.1

173.230.99.11和173.230.44.88分别是linode分配给你的ip
  
173.230.99.1和173.230.44.1分别是linode分配给你的网关

Ctrl + X, Ctrl +S 保存，然后重启一下Linode的机器，在Dashboard界面上就能完成。
  
重启之后应该完成了多个IP地址的配置。

在这之前建议先自己检查一下配置，不要拼错了，否则可能无法远程登录到机器上了。
  
如果你不熟悉这个过程的话，可以考虑删了机器重来:-P

多个站点的配置
  
登录Linode的Debian，首先运行一下apt-get update，更新一下源，安装Apache2，php5，mysql和phpmyadmin:
  
apt-get install apache2 mysql-server php5 phpmyadmin php5-gd
  
安装完成后基本上都能用了，但是phpmyadmin貌似缺少了一个快捷方式，apache2的默认运行根目录是/var/www
  
phpmyadmin的安装目录是/usr/share/phpmyadmin
  
运行这个 ln -s /usr/share/phpmyadmin /var/www/phpmyadmin
  
现在打开浏览器，访问：http://ip/phpmyadmin 就能访问phpmyadmin了

apache2的安装目录在/etc/apache2/下面，要配置多个站点，首先要编辑一个配置文件
  
/etc/apache2/sites-available/ 就是所有站点的配置信息，我们把default拷贝一份
  
cp default shootsoft.net
  
然后用emacs打开shootsoft.net这个配置文件
  
把 DocumentRoot /var/www/ 后面的路径改为我们的站点根目录，比如 /var/web/shootsoft
  
后面的：<Directory /var/www/> 里面的路径也一样改掉。
  
另外在DocumentRoot 这一行之上加上两行

> ServerName www.shootsoft.net
  
> ServerAlias shootsoft.net

然后在site-enabled目录下创建一个shootsoft.net的快捷方式
  
ln -s /etc/apache2/sites-available/shootsoft.net /etc/apache2/sites-enabled/shootsoft.net
  
重启apache
  
/etc/ini.d/apache2 restart
  
然后就生效了。
  
如果有更多的站点，可以效仿shootsoft.net的配置去修改

另外要注意的就是自己创建的站点目录，比如/var/web/shootsoft可能缺少权限，运行一下：

> chmod 777 /var/web/shootsoft

就OK了。