---
id: 117
title: Erlang的运算符(比较运算符,数值运算符,移位运算符,逻辑运算符)
date: 2011-02-22T12:50:13+00:00
author: admin
layout: post
guid: 'http://www.shootsoft.net/2011/erlang%e7%9a%84%e8%bf%90%e7%ae%97%e7%ac%a6%e6%af%94%e8%be%83%e8%bf%90%e7%ae%97%e7%ac%a6%e6%95%b0%e5%80%bc%e8%bf%90%e7%ae%97%e7%ac%a6%e7%a7%bb%e4%bd%8d%e8%bf%90%e7%ae%97%e7%ac%a6%e9%80%bb%e8%be%91/'
categories:
  - Erlang
tags:
  - Erlang
  - 数值运算符
  - 比较运算符
  - 移位运算符
  - 运算符
  - 逻辑运算符
---
参考：<http://www.erlang.org/doc/reference_manual/expressions.html>

Erlang的比较运算符

<table border="1" cellspacing="0" cellpadding="0">
  <tr>
    <td style="width: .6673in;">
      op
    </td>
    
    <td style="width: 120px;">
      Description
    </td>
  </tr>
  
  <tr>
    <td style="width: .6673in;">
      ==
    </td>
    
    <td style="width: 120px;">
      等于
    </td>
  </tr>
  
  <tr>
    <td style="width: .6673in;">
      /=
    </td>
    
    <td style="width: 120px;">
      不等于
    </td>
  </tr>
  
  <tr>
    <td style="width: .6673in;">
      =<
    </td>
    
    <td style="width: 120px;">
      小于等于
    </td>
  </tr>
  
  <tr>
    <td style="width: .6673in;">
      <
    </td>
    
    <td style="width: 120px;">
      小于
    </td>
  </tr>
  
  <tr>
    <td style="width: .6673in;">
      >=
    </td>
    
    <td style="width: 120px;">
      大于等于
    </td>
  </tr>
  
  <tr>
    <td style="width: .6673in;">
      >
    </td>
    
    <td style="width: 120px;">
      大于
    </td>
  </tr>
  
  <tr>
    <td style="width: .6673in;">
      =:=
    </td>
    
    <td style="width: 120px;">
      精确的等于
    </td>
  </tr>
  
  <tr>
    <td style="width: .6673in;">
      =/=
    </td>
    
    <td style="width: 120px;">
      精确的不等于
    </td>
  </tr>
</table>

<div style="clear: both;">
</div>

<div style="clear: both;">
  等于和精确等于的区别：
</div>

如果要比较两个数，如果两个数之间是不同的类型，比如float和int那么，==操作会首先把两个数字转换成相同的相同类型。举例：

1> 1==1.0.
  
true
  
2> 1=:=1.0.
  
false

所以一般推荐用精确等于去比较

比较运算符的大小级别：

number < atom < reference < fun < port < pid < tuple < list < bit string

3> 1 > a.

false

<table border="1" cellspacing="0" cellpadding="0">
  <tr>
    <td style="width: .7298in;">
      op
    </td>
    
    <td style="width: 198px;">
      Description
    </td>
    
    <td style="width: 149px;">
      Argument type
    </td>
  </tr>
  
  <tr>
    <td style="width: .7298in;">
      +
    </td>
    
    <td style="width: 198px;">
    </td>
    
    <td style="width: 149px;">
      number
    </td>
  </tr>
  
  <tr>
    <td style="width: .7298in;">
      &#8211;
    </td>
    
    <td style="width: 198px;">
    </td>
    
    <td style="width: 149px;">
      number
    </td>
  </tr>
  
  <tr>
    <td style="width: .7298in;">
      +
    </td>
    
    <td style="width: 198px;">
    </td>
    
    <td style="width: 149px;">
      number
    </td>
  </tr>
  
  <tr>
    <td style="width: .7298in;">
      &#8211;
    </td>
    
    <td style="width: 198px;">
    </td>
    
    <td style="width: 149px;">
      number
    </td>
  </tr>
  
  <tr>
    <td style="width: .7298in;">
      *
    </td>
    
    <td style="width: 198px;">
    </td>
    
    <td style="width: 149px;">
      number
    </td>
  </tr>
  
  <tr>
    <td style="width: .7298in;">
      /
    </td>
    
    <td style="width: 198px;">
      浮点数除法，结果是浮点数
    </td>
    
    <td style="width: 149px;">
      number
    </td>
  </tr>
  
  <tr>
    <td style="width: .7298in;">
      bnot
    </td>
    
    <td style="width: 198px;">
      一元not运算符
    </td>
    
    <td style="width: 149px;">
      integer
    </td>
  </tr>
  
  <tr>
    <td style="width: .7298in;">
      div
    </td>
    
    <td style="width: 198px;">
      整数除法，结果是整数
    </td>
    
    <td style="width: 149px;">
      integer
    </td>
  </tr>
  
  <tr>
    <td style="width: .7298in;">
      rem
    </td>
    
    <td style="width: 198px;">
      求玉树
    </td>
    
    <td style="width: 149px;">
      integer
    </td>
  </tr>
  
  <tr>
    <td style="width: .7298in;">
      band
    </td>
    
    <td style="width: 198px;">
      and运算
    </td>
    
    <td style="width: 149px;">
      integer
    </td>
  </tr>
  
  <tr>
    <td style="width: .7298in;">
      bor
    </td>
    
    <td style="width: 198px;">
      or运算
    </td>
    
    <td style="width: 149px;">
      integer
    </td>
  </tr>
  
  <tr>
    <td style="width: .7298in;">
      bxor
    </td>
    
    <td style="width: 198px;">
      xor异或运算
    </td>
    
    <td style="width: 149px;">
      integer
    </td>
  </tr>
  
  <tr>
    <td style="width: .7298in;">
      bsl
    </td>
    
    <td style="width: 198px;">
      左移位操作
    </td>
    
    <td style="width: 149px;">
      integer
    </td>
  </tr>
  
  <tr>
    <td style="width: .7298in;">
      bsr
    </td>
    
    <td style="width: 198px;">
      右移位操作
    </td>
    
    <td style="width: 149px;">
      integer<span style="font-size: 13px; line-height: 19px;"> </span>
    </td>
  </tr>
</table>

逻辑运算符

<table border="1" cellspacing="0" cellpadding="0">
  <tr>
    <td style="width: .6673in;">
      op
    </td>
    
    <td style="width: 120px;">
      Description
    </td>
  </tr>
  
  <tr>
    <td style="width: .6673in;">
      not
    </td>
    
    <td style="width: 120px;">
      一元逻辑not
    </td>
  </tr>
  
  <tr>
    <td style="width: .6673in;">
      and
    </td>
    
    <td style="width: 120px;">
      逻辑and
    </td>
  </tr>
  
  <tr>
    <td style="width: .6673in;">
      or
    </td>
    
    <td style="width: 120px;">
      逻辑or
    </td>
  </tr>
  
  <tr>
    <td style="width: .6673in;">
      xor
    </td>
    
    <td style="width: 120px;">
      逻辑xor
    </td>
  </tr>
</table>

<div style="clear: both;">
</div>

<div style="clear: both;">
  原子true 和false表示逻辑的&#8221;真&#8221;和&#8221;假&#8221;
</div>

此外，逻辑运算符还包括一个orelse 和andalso

原始的or和and是不带&#8221;短路运算&#8221;操作的，而orelse和andalso是带短路运算操作的。

短路运算举例

Express1 and Express2

Express1 andalso Express2

如果Express1 为假，and会继续判断Express2，然后整体判定为假，而andalso&#8221;短路&#8221;操作，直接判定整个表达式为假，从效率上来说，andalso会高一些