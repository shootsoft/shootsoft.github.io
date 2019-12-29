---
id: 147
title: '[Erlang] Unable to load crypto library Windows下的解决办法'
date: 2011-10-23T09:35:51+00:00
author: admin
layout: post
guid: http://www.shootsoft.net/?p=147
categories:
  - Erlang
tags:
  - Erlang
  - Unable to load crypto library
---
在一台64位的Widnows2008上，安装了Erlang之后，运行erl，测试几条erlang语句，一切正常。但是在试图启动一个使用了SSL类库的应用程序时，出现了如下的提示：

> Unable to load crypto library. Failed with error:
> 
> &#8220;load_failed, Failed to load NIF library c:/PROGRA~2/ERL58~1.2/lib/crypto-2.0.2/
> 
> priv/lib/crypto: &#8216;Unspecified error'&#8221;
> 
> OpenSSL might not be installed on this system.
> 
> &#8220;(pubSageService@Apptest2)1> i
> 
> =ERROR REPORT==== 21-Oct-2011::09:47:29 ===
> 
> The on_load function for module crypto returned {error,
> 
> {load_failed,
> 
> &#8220;Failed to load NIF library c:
> 
> /PROGRA~2/ERL58~1.2/lib/crypto-2.0.2/priv/lib/crypto: &#8216;Unspecified error'&#8221;}}
> 
> n(pubSageService@Apptest2)1> it terminating in do_boot&#8221;,{undef,[{crypto,start,[]
> 
> },{init,start\_it,1},{init,start\_em,1}]}}
> 
> &nbsp;
> 
> Crash dump was written to: erl_crash.dump
> 
> init terminating in do_boot ()

该机器已经安装了64位的OpenSSL类库（下载<http://www.slproweb.com/products/Win32OpenSSL.html>）

Google之后找到了一篇Google Groups上面的讨论文章

<http://groups.google.com/group/erlang-programming/browse_thread/thread/288684b61116baf3>

首先怀疑Win32的 OpenSSL类库安装的有问题，于是重新安装了一遍，之前安装的忘记最后一步是否选择了将OpenSSL的类库拷贝打到系统目录下（Windows\System32\）,重新安装的时候确认拷贝，但是启动仍然失败。

接下来又把那几个dll拷贝到Erlang的安装目录（就是上面的提示的那个目录）：

> c:/PROGRA~2/ERL58~1.2/lib/crypto-2.0.2/priv/lib/crypto

这个是缩写的目录，实际是：

> C:\Program Files (x86)\erl5.8.2\lib\crypto-2.0.2\priv\lib

这次换了个错误提示：

> Unable to load crypto library. Failed with error:
> 
> &#8220;load_failed, Failed to load NIF library c:/PROGRA~2/ERL58~1.2/lib/crypto-2.0.2/
> 
> priv/lib/crypto: &#8216;Unspecified error'&#8221;
> 
> OpenSSL might not be installed on this system.
> 
> &#8220;(pubSageService@Apptest2)1> i
> 
> =ERROR REPORT==== 21-Oct-2011::09:47:29 ===
> 
> The on_load function for module crypto returned {error,
> 
> {load_failed,
> 
> &#8220;Failed to load NIF library c:
> 
> /PROGRA~2/ERL58~1.2/lib/crypto-2.0.2/priv/lib/crypto: &#8216;Unspecified error'&#8221;}}
> 
> n(pubSageService@Apptest2)1> it terminating in do_boot&#8221;,{undef,[{crypto,start,[]
> 
> },{init,start\_it,1},{init,start\_em,1}]}}
> 
> &nbsp;
> 
> Crash dump was written to: erl_crash.dump
> 
> init terminating in do_boot ()

又仔细看了一遍帖子，怀疑是64的OpenSSL和64位的Windows 2008不兼容，于是重新安装了一个32位的，一切正常~