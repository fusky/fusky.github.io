---
layout: post
title: Nodejs简单入门
category:  技术
tags: Nodejs
description:  Nodejs 建立简单 web 服务。
---

> Mac下搭建Nodejs 开发环境，进行简单的编程，仅做一个Nodejs入门。

#####Nodejs下载地址：[点击下载](http://nodejs.org/)
在Nodejs 官网点击 install 即可下载 Nodejs 安装，非常简单。安装过程中可能需要管理员权限，输入管理员密码即可。可以在命令行下输入一下命令查看安装版本。

     node --version
    
如果不可以，请尝试：
      
     sudo node --version
    
如果安装成功，你不仅可以使用 node 命令运行 nodejs 程序还可以使用 npm 命令。npm 是 nodejs 的包管理工具，安装扩展包十分方便，之前的版本需要自己独立安装，现在直接集成在nodejs 中。npm 安装包的命令格式如下：

    sudo npm install xxx
    
可以通过使用下面命令查看 npm 的参数和使用方法。

    sudo npm --help
    
    where <command> is one of:
    add-user, adduser, apihelp, author, bin, bugs, c,
    cache, completion, config, ddp, dedupe, deprecate,
    docs, edit, explore, faq, find, find-dupes, get, help,
    help-search, home, i, info, init, install, isntall,
    issues, la, link, list, ll, ln, login, ls, outdated,
    owner, pack, prefix, prune, publish, r, rb, rebuild,
    remove, repo, restart, rm, root, run-script, s, se,
    search, set, show, shrinkwrap, star, stars, start,
    stop, submodule, t, tag, test, tst, un, uninstall,
    unlink, unpublish, unstar, up, update, v, version,
    view, whoami 
    (上面是 npm 的命令，可以通过下面的参数详细查看说明)

    npm <cmd> -h     quick help on <cmd>
    npm -l           display full usage info
    npm faq          commonly asked questions
    npm help <term>  search for help on <term>
    npm help npm     involved overview
    
## 第一个nodejs 程序

Nodejs 不需要类似 Apache 等的服务器软件就可以开启 web 服务，非常的方便，我们今天简单地写一个网页作为 nodejs 的入门，在浏览器中输出 Hello Nodejs！

    var http = require('http');
    http.createServer(function(req,res) {
			res.writeHead(200, {'Content-type': 'text/html'});
			res.write('<h1>Node.js</h1>');
			res.end('<p>Hello Choggle!</p>');
		}).listen(3000);
    console.log("HTTP server is listening at port 3000.");
    
保存上边的代码为 js 文件，然后在终端运行，打来浏览器输入127.0.0.1：3000，体验一下吧。

    sudo node hello.js
    

