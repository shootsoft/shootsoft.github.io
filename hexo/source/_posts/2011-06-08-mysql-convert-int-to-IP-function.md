---
id: 124
title: mysql int整型转换为 IP地址的自定义函数
date: 2011-06-08T16:54:43+00:00
author: admin
layout: post
categories:
  - MySQL
tags:
  - int转换
  - ip
  - MySQL
  - 自定义函数
---
碰到IP地址与Int转换的问题，得到了一个csv格式的ip列表，但是ip地址却是int格式。因为使用的时候主要是在数据库里使用，所以写个程序转换一把有些麻烦，后来想到mysql里面有自定义函数，于是尝试了一把，顺利解决:-)

```
DELIMITER $$
  USE `iptest`$$
  DROP FUNCTION IF EXISTS `int2ip`$$
  CREATE DEFINER=`root`@`%` FUNCTION `int2ip`(num BIGINT) RETURNS VARCHAR(255) CHARSET utf8BEGIN 
    DECLARE result VARCHAR(255);
    SET result = CONCAT(CAST((num DIV 16777216% 256) AS SIGNED), ‘.’, CAST(num DIV 65536 % 256 AS SIGNED ), ‘.’, CAST(num DIV 256%256 AS SIGNED ), ‘.’, CAST(num%256 AS SIGNED ));
    RETURN result;
  END$$
DELIMITER ;
```

使用的时候：

```
Select int2ip(`ip`) from table;
```

附int整型和ip转换的公式，摘自：<a href="http://www.shootsoft.net/129">Linux(Debian)下正确编译安装Erlang的方法</a>


```
IP Address = 202.186.13.4
w = 202, x = 186, y = 13 and z = 4
INT IP Number = 16777216*202 + 65536*186 + 256*13 + 4
= 3388997632 + 12189696 + 3328 + 4
= 3401190660
```
  
INT 转 IP:

```
w = int ( IP Number / 16777216 ) % 256
x = int ( IP Number / 65536 ) % 256
y = int ( IP Number / 256 ) % 256
z = int ( IP Number ) % 256
```