---
layout: post
title: Tinyeditor
category:  技术
tags: tinyeditor
description:  Tinyeditor的使用。
---

##Tinyeditor  选择
  
因为开发了一个卖水果的微信账号，需要使用网页编辑器编辑水果详情介绍，找了网上的资源，起初准备采用百度的 Uediter编辑器，但是看了下接入步骤太多了，而且功能过于强大，于是放弃了。突然间就看到了 Tinyeditor，简单小巧、功能齐全。果断选择 tinyeditor 进行开发，tinyeditor 长相如下。
![tinyeditor](https://raw.githubusercontent.com/fusky/fusky.github.io/master/public/img/tinyeditor.png)

##Tinyeditor 介绍

今天要给大家推荐的TinyEditor，是国外知名Web设计博客leigeber.com刚发布的一款简洁且易用的html所见即所得编辑器。它使用Javascript编写，不依赖于其它类库这是一个轻量级的编辑器，要调用的文件仅有8kb它可以处理大多数的html格式化需求，并且内置的功能使得生成的标记尽量简洁编辑器中用到的小图标使用了CSS Sprite技术，减少了http连接在主流浏览器中测试通过可个人或商业项目中使用，遵循creative commons license.

##Tinyeditor 使用

1. 在网页中引用 TinyEditor 提供的 js 文件和 css 文件。
2. 在网页中添加标签，就是个 textarea 标签。
  <textarea id=“input” style=“width:400px; height:200px”></textarea>
3. 初始化编辑器，配置参数。
	new TINY.editor.edit(‘editor’,{
		id:’input’, 
	// (必须)上面第二步中定义的textarea的id
		width:584, 
	// (选填) 编辑器宽度
		height:175,
	 // (选填) 编辑器高度
		cssclass:’te’,
	 // (选填) 编辑器的class，用来通过css控制样式
		control class:’decontrol’,
	 // (选填) 编辑器上按钮的class
		row class:’teheader’,
	 // (选填) 编辑器按钮行的class
		dividerclass:’tedivider’, 
	// (选填) 编辑器按钮间分割线的样式
		controls:[‘bold’, ‘italic’, ‘underline’, ‘strikethrough’, ‘|’, ‘subscript’, ‘superscript’, ‘|’, ‘ordered list’, ‘unordered list’, ‘|’ ,’outdent’ ,’indent’, ‘|’, ‘left align’, ‘center align’, ‘right align’, ‘block justify’, ‘|’, ‘unformed’, ‘|’, ‘undo’, ‘redo’, ’n’, ‘font’, ‘size’, ‘style’, ‘|’, ‘image’, ‘hr’, ‘link’, ‘unlink’, ‘|’, ‘cut’, ‘copy’, ‘paste’, ‘print’],
	 // (必须) 要根据需要在编辑器上添加按钮控件, 其中’|’代表功能按钮间的竖分割线，’n’代表按钮行间的分割线
		footer:true, 
	// (选填) 是否显示编辑器底部
		fonts:[‘Verdana’,’Arial’,’Georgia’,’Trebuchet MS’],  
	// (选填) 编辑器中可选择的字体
		xhtml:true, 
	// (选填) 编辑器生成xhtml还是html标记
		cssfile:’style.css’, 
	// (选填) 要为编辑器附加的外部css文件
		content:’starting content’, 
	// (选填) 设置编辑器编辑区域中的初始内容
		css:’body{background-color:#ccc}’,
	 // (选填) 设置编辑器编辑区域背景
		bodied:’editor’, 
	// (选填) 设置编辑区域ID
		footer class:’tefooter’, 
	// (选填) 设置编辑器底部class
		toggle:{text:’源代码’,active text:’可视化’,cssclass:’toggle’},
	 // (选填) 设置源代码浏览切换文字，及切换按钮的class
		resize:{cssclass:’resize’} 
	// (选填) 设置编辑器大小调整按钮的class
	});

PS:在使用的时候记得调用 instance.post()函数，以确保编辑区域中最新的可视化内容转换为标记文本。在上面的实例中就是在提交的 button 标签中设置 onclick=“input.post()”。

[下载源代码](http://www.websbook.com/upimg/allimg/100224/tinyeditor.zip)