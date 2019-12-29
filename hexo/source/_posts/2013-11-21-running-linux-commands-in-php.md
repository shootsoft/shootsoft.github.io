---
id: 221
title: PHP在Linux下运行Shell命令
date: 2013-11-21T15:57:59+00:00
author: admin
layout: post
guid: http://www.shootsoft.net/?p=221
categories:
  - Linux
tags:
  - Java
  - Linux
  - PHP
  - Shell
---
原本在本机开发PHP的时候，Shell调用一切正常。上线的时候才反应到线上的服务器对权限做了严格的控制，一顿折腾之后梳理出在严格权限控制的Linux上如何通过Nginx/Apache 以Web的方式调用Shell命令，比如调用java编译或者执行java程序。

Web服务器使用www用户启动。分为两种情况：一种是命令是通过root安装的，并不能直接把权限直接赋给www用户，比如/usr/local/nginx/sbin/nginx；一种是www用户对要执行的命令有绝对的权限，但是由于缺少某些环境变量，执行的程序如果用到了这些变量就得提前再次设定环境变量。

先说第一种，其实php.ini里面已经定义了不可以调用的命令，默认情况下exec, system之类都不能执行。首先要去php.ini里面把

> disable_functions=

这一项里面定义的那些调用Shell脚本的函数移出列表，然后重启Nginx的PHP-PFM或者Apache。可以测试一下

> <?php echo exec(&#8220;pwd&#8221;); ?>

正常情况下应该就可以看到当前的路径信息了。但是要想执行一些root才能执行的命令，比如重新加载Nginx配置文件，还需要一些额外的操作，这里参考<http://bbs.chinaunix.net/thread-3693263-1-1.html>

> 1、设置 sudo 配置文件 可写权限
  
> chmod u+w /etc/sudoers
> 
> 2、增加 www 用户的 nginx 脚本管理权限
  
> www     ALL=(root)      NOPASSWD: /etc/init.d/nginx
> 
> 3、关闭 【强制控制台登录】执行
  
> 【非常重要】，注释该行 我的问题就出在这里，开启了这个选项之后。在PHP中怎么调用，都没有执行结果
  
> #Defaults    requiretty
> 
> 4、还原 sudo 配置权限  440
  
> 【非常重要】，如果不还原权限。在PHP中怎么调用，都没有执行结果。
  
> chmod u-w /etc/sudoers
> 
> 5、调用php
  
> $result2 = exec(&#8220;/usr/bin/sudo /etc/init.d/nginx stop&#8221;,$result);
  
> var_dump($result);
  
> var_dump($result2);

再看看如果调用Java编译并执行。www用户拥有对/work/java目录的执行权限。直接上代码：

Java的，文件名&#8221;TestJava.java&#8221;

> public class TestJava{
  
> public static void main(String[] args) {
  
> System.out.println(&#8220;Hello World!&#8221;);
  
> }
  
> }

PHP的，文件名&#8221;test.php&#8221;

> <?php
> 
> function del_file($file){
  
> if(file_exists($file) && unlink($file) ){
  
> echo &#8220;del &#8220;.$file.&#8221;<br />\r\n&#8221;;
  
> }
  
> }
> 
> function execute($exe){
  
> echo $exe.&#8221;<br />\r\n&#8221;;
  
> $r=exec($exe, $res);
  
> var_dump($res);
  
> echo &#8220;<br />&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-<br />\r\n&#8221;;
  
> var_dump($r);
  
> echo &#8220;<br />&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-<br />\r\n&#8221;;
  
> }
> 
> $target_file = &#8220;TestJava.class&#8221;;
  
> $output_file = &#8220;output.txt&#8221;;
  
> $src=&#8221;/work/web/services.adsage.com/deploy/monitor/test/TestJava.java&#8221;;
  
> $bin=&#8221;TestJava&#8221;;
  
> $jcommon = &#8220;export JAVA\_HOME=/work/java\nexport JRE\_HOME=$JAVA\_HOME/jre\nexport PATH=$JAVA\_HOME/bin:$PATH\n/work/java/bin/&#8221;;
  
> $javac=$jcommon.&#8221;javac &#8220;.$src;
  
> $javab=$jcommon.&#8221;java &#8220;.$bin.&#8221; >> &#8220;.$output_file;
  
> del\_file($target\_file);
  
> del\_file($output\_file);
> 
> execute($javac);
  
> execute($javab);
> 
> echo &#8220;final:<br />\r\n&#8221;;
  
> $output=file\_get\_contents($output_file);
  
> echo $output;
  
> ?>

通过Web浏览结果：

> del TestJava.class
  
> del output.txt
  
> export JAVA\_HOME=/work/java export JRE\_HOME=/jre export PATH=/bin: /work/java/bin/javac /work/web/services.adsage.com/deploy/monitor/test/TestJava.java
  
> array(0) { }
  
> &#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-
  
> string(0) &#8220;&#8221;
  
> &#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-
  
> export JAVA\_HOME=/work/java export JRE\_HOME=/jre export PATH=/bin: /work/java/bin/java TestJava >> output.txt
  
> array(0) { }
  
> &#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-
  
> string(0) &#8220;&#8221;
  
> &#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-
  
> final:
  
> Hello World!

&nbsp;