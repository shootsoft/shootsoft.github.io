---
id: 86
title: 如何编写支持Lucene.NET的中文分词程序
date: 2010-08-01T05:39:08+00:00
author: admin
layout: post
guid: http://www.shootsoft.net/?p=86
categories:
  - Others
---
近来很多朋友都给我写信询问如何把ShootSearch中文分词组件支持dotlucene,因为杂七杂八的事太多，所以一直没顾上，这两天研究了一下，发现其实很简单。

首先说明一下dotlucene的中文分词程序。我一开始接触dotlucene时，是1.4的版本，那个版本是支持中文分词的。一开始我还不太明白，后来发现那个StandardAnalyzer对中文的处理是按字去分，而非词。原来1.3版时dotlucene是不支持处理中文的！于是我就开始搜索支持中文按词分的程序，lucene的很多，但是dotlucene的却凤毛麟角，于是就产生了写一个中文分词程序的想法，后来看了一些文章后就有了ShootSearch中文分词组件。这个分词程序是最大匹配分词。

要想写支持dotlucene的中文分词程序一定要看的是这个Lucene.Net.Analysis.Cn，它是dotlucene1.3版时处理中文的分词组件。只要继承Analyzer，TokenFilter，Tokenizer这三个类即可，最低要求是Analyzer和Tokenizer这两个类，因为TokenFilter是用来处理噪声词的（就是单个的“的”“啊”“是”之类的词），暂时可以不管它。

Analyzer的继承是最简单的，只有3，4行代码，只需覆盖一个非常简单的方法TokenStream，参考我写的ShootAnalyzer即可，Tokenizer的继承稍微复杂一点点，因为这个是处理分词过程的类，不过实际上要是你的分词部分已经写好了的话也就几行代码万事！要覆盖的方法除了构造方法就是Next（）方法，它的用意是返回一个词（Token），有点像数据库的游标一样，要是返回null就表示没有词了。Token的构造方法也很简单，返回一个字符串，和前后位置即可。大家如果有耐心的话可以仔细读一下Lucene.Net.Analysis.Cn的代码，Next（）一次就是返回一个字而已。稍微把Segment.cs改造一下就可以很好地处理这个问题了，目前我的方法是增加了一个Ends属性，它存储的是一个int组，内容就是每个词的结束符地址。具体代码请大家参考一下我的ShootTokenizer吧，也就10来行代码，注释基本清晰。

最后要说一下,java的lucene下面有很多支持中文的分词程序,如果有需要的话可以尝试移植一下.

所有代码请到这里下载：http://www.shootsoft.net/index.php/2010/08/shootsearch-segment-070312/