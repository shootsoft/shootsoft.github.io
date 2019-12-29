---
id: 213
title: 通过TestFlightApp.com管理团队测试设备
date: 2013-10-19T11:41:09+00:00
author: admin
layout: post
guid: http://www.shootsoft.net/?p=213
categories:
  - Download
  - News
tags:
  - Casperjs
  - TestFlight
  - 开源
  - 设备列表
---
最近团队正在尝试使用Test Flight来管理测试App和内部Demo的分发。使用Test Flight最大的好处就是可以让不越狱的iOS设备免费使用Test Flight的企业证书。

之前团队碰到过一个Android测试设备的管理问题：作为一个创业团队，没有财力购买多余的设备。虽然每个测试，研发以及销售、运营同事都有自己的设备，但是在很多情况下，这些设备作为测试设备临时征用的时候就碰到一些困难，无法完整统计每个人手里的设备型号。

在使用Test Flight的时候发现Test Flight不仅仅可以用来分发测试App，同时也收录了所有测试人员手中的设备情况。但是Test Flight没有提供直观的视图来让测试、开发或者管理员来统计所有的设备情况。

仔细琢磨了一下，花了点时间，写了个CasperJS的脚本，来登录Test Flight并且把所有的测试设备列表抓取回来。

源码：<https://github.com/shootsoft/testflight-device>

使用：

> casperjs device.js &#8211;username=xxxx &#8211;password=yyyy >> device.csv

device.csv可以用Excel导入形成直观的表格

> email,platform,hardware,os,udid
  
> a@xxxcom,Android,Xiaomi MI 2SC (Phone),Android 4.1.1,
  
> b@xxxcom,iOS,iPod Touch 4th Gen,iOS 6.1.2,3660axxxxx28986c9e96c6c822e7c7049
  
> c@xxxcom,Android,Samsung GT-I9502 (Phone),Android 4.2.2,
  
> c@xxxcom,Android,Huawei HUAWEI Y220-T10 (Phone),Android 2.3.5,
  
> d@xxxcom,Android,Huawei HUAWEI U8825D (Phone),Android 4.0.4,
  
> e@xxxcom,iOS,iPad 2 Wi-Fi,iOS 6.1.3,60301xxxxxxxxff4cab91db6325cc7
  
> e@xxxcom,Android,Lenovo Lenovo A820e (Phone),Android 4.1.2,
  
> f@xxxcom,Android,Htc Evo 3D GSM (Phone),Android 4.1.2,
  
> f@xxxcom,iOS,iPhone 4 GSM,iOS 5.1.1,ae3b3fxxxxxxxxxx5c71aa5f6ff3d59c1f921
  
> g@xxxcom,iOS,iPhone 4S,iOS 7.0.2,178215cxxxx36d0eb48e2b54bfe3c5077

导入Excel后

<p style="text-align: center;">
  <a href="http://www.shootsoft.net/wp-content/uploads/2013/10/testflightapp-device-excel.png"><img class="wp-image-214 alignleft" alt="testflightapp-device-excel" src="http://www.shootsoft.net/wp-content/uploads/2013/10/testflightapp-device-excel.png" width="654" height="146" srcset="https://www.shootsoft.net/wp-content/uploads/2013/10/testflightapp-device-excel.png 909w, https://www.shootsoft.net/wp-content/uploads/2013/10/testflightapp-device-excel-300x66.png 300w" sizes="(max-width: 654px) 100vw, 654px" /></a>
</p>