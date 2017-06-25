---
layout: post
title:  Mac上brew安装Python和mysqlclient
date:   2017-06-25 14:46:25 +0800
categories:
- Python
- Django
- MySQL
- Mac
---

今日想研究下`Django`框架，需要配置合适的`Python`环境。虽然`Mac`系统默认安装了`Python`，但由于各种系统权限问题，导致安装各种库时会出现很多奇奇怪怪的问题。因此，推荐使用`brew`另外安装一个`Python`，这样各种控制就很灵活了。

1. `brew install python`安装`Python 2.7`；
2. 输入命令验证安装，如果`which python` 返回 `/usr/local/bin/python`和`which easy_install` 返回 `/usr/local/bin/easy_install`，证明安装正确；
3. 通过easy_install安装pip `easy_install pip`；
4. `Python`默认支持`SQLite`，但平时使用最多是`MySQL`，需要安装`mysqlclient`，`pip install mysqlclient`；
5. 如果安装过程中提示`not found mysql_config`，就需要将`export PATH="$PATH":/usr/local/mysql/bin`添加到`.bash_profile`或者`.zshrc`中，再执行`pip install mysqlclient`就可以安装了；
6. 如果在链接`MySQL`时提示`Library not loaded: libmysqlclient.18.dylib`，就需要将`export DYLD_LIBRARY_PATH="$DYLD_LIBRARY_PATH:/usr/local/mysql/lib/"`添加到`.bash_profile`或者`.zshrc`中就可以了。
