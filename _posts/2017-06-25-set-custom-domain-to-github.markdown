---
layout: post
title:  设置自定义域名到Github
date:   2017-06-25 13:28:55 +0800
categories:
- Github
---

1. 注册一个域名，例如：`elrichuang.com`；
2. 在Github page的网站根目录下新建一个名为`CNAME`的文件并上传到`github.io`对应的网站上；（注意文件名大小写且没有后缀名）
3. 在域名服务商的域名管理后台添加两条`CNAME`类型的域名解析记录，设置如下：

| 记录类型 | 主机记录 | 记录值 |
| ------- | ------- | ------ |
| CNAME   | @       | `elrichuang.github.io` |
| CNAME   | www     | `elrichuang.github.io` |

4. 推荐使用`CNAME`方式绑定，不建议使用`A记录`的方式绑定`github.io`的`IP`，因为`IP`有可能会变。