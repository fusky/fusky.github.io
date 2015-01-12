---
layout: post
title: jekyll使用多说评论
category:  技术
tags: [技术 , jekyll , 多说]
description:  使用多说作为 Jekyll 博客的评论插件。
---

很多程序员都喜欢使用 github 提供的服务，自然对于 Jeklly 肯定不会陌生。我们可以使用 Jeklly 免费在 github 上面部署一个静态博客，并且可以很方便的绑定自己的域名。 在 github 上面有许许多多免费的 Jeklly 博客主题，加上国内访问 github 的速度也很 OK，所以对于喜欢写东西的程序员来说搭建一个 Jeklly 博客是一个不错的选择。

[Jeklly 主题下载](http://jekyllthemes.org/)

但是对于原生的 Jeklly 使用的评论管理工具是国外的DISQUS，国内的访问速度不是很理想，而且也不支持国内的社交账号登陆，所以我想把评论插件改成国内比较流行的**多说**。我先在网上找了一些教程，但是教程不是很适合，Jeklly 有些内容更改了，我尝试这自己摸索，最后成功使用多说，详细教程如下。

首先去多说网站注册一个账号，注册成功之后创建一个站点，你会得到一个二级域名，类似 http://xiaochaolee.duoshuo.com/admin 的一个管理地址，记住` xiaochaolee`，这是待会我们要使用的`shortname`值。然后你会得到如下的代码：

    <!-- 多说评论框 start -->
	<div class="ds-thread" data-thread-key="请将此处替换成文章在你的站点中的ID" data-title="请替换成文章的标题" data-url="请替换成文章的网址"></div>
<!-- 多说评论框 end -->
<!-- 多说公共JS代码 start (一个网页只需插入一次) -->
<script type="text/javascript">
var duoshuoQuery = {short_name:"xiaochaolee"};
	(function() {
		var ds = document.createElement('script');
		ds.type = 'text/javascript';ds.async = true;
		ds.src = (document.location.protocol == 'https:' ? 'https:' : 'http:') + '//static.duoshuo.com/embed.js';
		ds.charset = 'UTF-8';
		(document.getElementsByTagName('head')[0] 
		 || document.getElementsByTagName('body')[0]).appendChild(ds);
	})();
	</script>
<!-- 多说公共JS代码 end -->

上面已将将我们的` shortname`设置好了，我们将下面的代码替换上面相应的位置：

    <!-- 多说评论框 start -->
    <div class="ds-thread" data-thread-key={{page.id}} data-title={{page.title}} data-url="iperson.cn{{page.url}}"></div>
<!-- 多说评论框 end -->

其中** iperson.cn **改成你自己的域名，然后将代码保存为 duoshuo.html 放到 _includes 目录下。

接下来修改 _comfig.yml 文件，找到 disqus 设置的地方，将下面的代码注释，并写上多说的配置选项。

    disqus:
     shortname: fusky
    替换为：
    duoshuo:
      shortname: iperson (上面注册多说账号时候的 shortname)
      
  然后修改 _layouts 目录下单 page.html 文件，将其中的 {% include disqus.html %} 替换为  {% include duoshuo.html %} 保存即可。
         
push 到你的仓库，查看网站看看效果吧！
    

    