---
layout: post
title:  Mac上brew安装ruby
date:   2017-06-25 14:54:12 +0800
categories:
- Ruby
- Mac
---

使用`Jekyll`需要`Ruby`环境，虽然`Mac`内置了`Ruby`，但由于权限等问题，安装`gem`时经常出现问题，因此一般使用`brew`另外安装一个`Ruby`。

1. 执行`brew install ruby`；
2. 安装完成后，执行`which ruby`显示`/usr/local/bin/ruby`就证明安装正确。安装`gem`只要简单的`gem install xxx`就可以了。