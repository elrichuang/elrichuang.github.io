---
layout: post
title:  使用Jekyll写Blog
date:   2016-03-20 20:45:27 +0800
categories: jekyll
---

![](https://jekyllrb.com/img/logo-2x.png)

`Jekyll`是`Github`官方出品的开源静态网站构建工具。使用它可以将你写的`Markdown`文本文件转换为一个静态网站或者博客。它主要是为了方便程序员构建基于`Github Pages`服务的静态网站而出现的。

### 安装

以博主使用的`Mac OS X 10.11`为例：

1. `Jekyll`是基于`Ruby`开发的，需要首先安装`Ruby`。幸运的是`Mac OS X`已经内置了`Ruby 2`，因此不用另外安装。
2. 在`Mac`的`终端`运行命令：`sudo gem install -n /usr/local/bin jekyll`，即会自动安装完成`Jekyll`。
3. 运行命令`jekyll new blog`，即会在当前文件夹建立一个新的blog文件夹，blog文件夹就是`jekyll`项目文件夹。
4. 运行命令`cd blog`进入项目文件夹。
5. 运行命令`jekyll serve`运行内置Web服务器程序，在浏览器打开`http://localhost:4000`就会看到网站内容了。![](/img/jekyll-home.jpg)
6. `Ctrl+C`停止Jekyll Web服务器运行。

### Jekyll项目文件夹结构

* `_config.yml`Jekyll项目配置文件。
* `_includes`是页面模版的一些公共部分，例如：header，footer之类的。
* `_layouts`页面模版。`default`是基础模版，`page`是单页面模版，继承`default`，例如：`about`页；`post`是文章内页模版，继承`default`。
* `_post`是文章内容。使用[Markdown](https://guides.github.com/features/mastering-markdown/)语法编写，一个文件一篇博文，文件名就是url访问地址。
* `_sass`是默认的模版样式设置文件。
* `_site`这个是重点！！！这里存放最终放到网上的完整的网站文件，相当于发布网站的根目录。
* `about.md`关于页面。
* `css`保存网站css文件。
* `feed.xml`RSS订阅文件。
* `index.html`网站首页模版。

![](/img/jekyll-folder-structure.jpg)

### 更新内容

* 除了修改了`_config.yml`文件的内容需要重新启动`jekyll serve`意外，其他页面修改了，在浏览器刷新即可看到效果。
* 在本地编写完博客后，在浏览器预览没有问题了，就可以发布网站了。

### 发布内容到github.io

1. 打开`终端`，切换到Jekyll项目的目录下，运行`jekyll build`生成发布网站内容。
2. 将`_site`目录下的所有内容复制到个人网站的服务器上或者xxx.github.io的git目录中，提交推送到服务器，网站发布成功。


