---
layout: post
title: PHP开发中的编码问题笔记
category:  技术
tags: [技术, PHP, 总结]
description:  PHP 开发过程中常用的编码问题总结和相关函数整理。
header-img: "img/php_bg.jpg"
---

**之前在项目中需要开发支付接口，涉及到 php 提交数据给 java 写的支付网关，在调试的过程中遇到了编码不一致的问题，于是整理了一下 PHP 开发过程中涉及到的编码问题。**

# 字符编码
关于字符编码通常只涉及 gbk 和 utf-8 这两种编码，如果网页打开的时候是乱码，或者从数据库中获取数据得到的是乱码或者取不到数据，通常都是因为字符编码设置不一致造成的。

- 1、设置 php 页面的编码

```
header(“Content-type: text/html; charset=utf-8”);
header(“Content-type: text/html; charset=gb2312”); 

```
上面这两行是分别将 php 页面编码设置成 utf-8 和 gbk 编码，同时保存 php 文件的时候也要选择对应的编码保存。这样基本不会再出现页面乱码的问题。

- 2、设置 mysql 数据库连接编码

```
mysql_query(“set character set ‘utf8’”);//读库
mysql_query(“set names ‘utf8’”);//写库

```
当从数据库读取到的中文是乱码的时候通常都是 php 编码和数据库的编码不一致造成的，通过上面的设置就可以解决中文数据乱码的问题。设置 gbk 编码只要对应设置就可以了。

- 3、内部编码
通常经过上面的设置一般不会出现字符编码的问题。还有一个设置 php 内部编码的函数，这是 http 默认输入输出编码方式。

```
<?php
/* 设置内部字符编码为 UTF-8 */
mb_internal_encoding(“UTF-8”);
/* 显示当前的内部字符编码*/
echo mb_internal_encoding();
?>
```

#  URL字符串编码
之前开发支付接口的时候遇到过 URL 编码的问题，类似【%E4%B8%AD%E6%96%87】这样的从名字也可以看出这是对网址的一种编码，我们在使用百度和 google 的时候会发现搜索引擎默认将中文进行了 url 编码，在做数据提交的时候浏览器也会将 post 提交的内容默认做 url 编码，所以我们有的时候从服务获取的数据也要做一下 url 解码。PHP 中涉及到 url 编码的函数有四个，分别是urlencode()、urldecode()、rawurlencode()、rawurldecode()，通常使用前两个就可以了。rulencoude() 和 rawurlencode() 的区别在于：

**urlencode 将空格则编码为加号（+***）
**rawurlencode 将空格则编码为加号（%20***）

~~目前涉及到的情况比较少，以后遇到新问题在更新整理~~



