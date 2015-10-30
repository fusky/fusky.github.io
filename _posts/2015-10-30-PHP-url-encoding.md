---
layout: post
title: PHP解析 URL 编码问题
category:  技术
tags: PHP URL
description:  PHP 开发过程中遇到 URL 编码问题的解析案例。
---

	这几天在做一个银行网关支付的项目，需要和银行网关进行支付等相关接口的对接。数据的传输采用的是 XML 格式，通过 POST 进行传输，这几乎是所有支付 API 都使用的方案，之前做过微信和宝付支付的接口开发都是这样的情况。
	这次的开发需要多费些功夫，因为没有SDK，同时也找不到相关的例子和代码，因为银行的网关支付刚刚上线，只能参考文档硬着头皮自己来，说实话我的经验并不丰富，也是半路出家学的 PHP，很多东西都不太清楚。
	经过查阅文档和网络资料，终于正确的发送了支付请求，结果在接收返回数据的时候遇到了问题，让自己手足无措。通过chrome 的开发者工具可以查看到接收的数据如下：

>%3CCSRCEBankData%3E%3CMessage+id%3D%22141011134131000001%22%3E%3CEBPRes+id%3D%22EBPRes%22%3E%3Cversion%3E1.0.0%3C%2Fversion%3E%3CinstId%2F%3E%3CcertId%3E0001%3C%2FcertId%3E%3CmerchantNo%3E100003%3C%2FmerchantNo%3E%3CorderNo%3E533378%3C%2ForderNo%3E%3CbankFlowNo%3EPY201510230110001562%3C%2FbankFlowNo%3E%3CorderTime%3E20141011134131%3C%2ForderTime%3E%3CorderAmt%3E3600%3C%2ForderAmt%3E%3Ccurrency%3E01%3C%2Fcurrency%3E%3CcardType%3ED%3C%2FcardType%3E%3CpayStatus%3E0001%3C%2FpayStatus%3E%3Cbanktime%3E20151023153346%3C%2Fbanktime%3E%3CnotifyId%3E100000001262pnL8Mkux%3C%2FnotifyId%3E%3Crem1%2F%3E%3Crem2%2F%3E%3C%2FEBPRes%3E%3CSignature%3E446aa0a6ea5a883db3645a26466ba24b%3C%2FSignature%3E%3C%2FMessage%3E%3C%2FCSRCEBankData%3E

我一看这是什么鬼，怎么会这样，想要把这个东西装换成 xml 数据，查了好久都不知如何下手，没办法我自己把**%3C**替换成**<**,以此类推，想要一点一点自己把它解析成 xml 各式的字符串，正在准备这样做的时候突然去查了一下%3C是什么编码，不查不知道，一查知道了这是 URL 编码的格式，PHP 有封装好的函数可以直接解析，就这样突然就解决了问题，只需要使用urldecode()函数就可以轻松将 URL 编码的字符串解析出来，然后再做一下处理就可以直接操作 XML 数据中的值了，其实非常的简单，只是因为自己的不知道走了许多弯路。

>多动脑筋，遇到问题的时候多试试总能有意外收获。