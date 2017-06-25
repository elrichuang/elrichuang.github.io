---
layout: post
title:  CodeIgniter Nginx配置
date:   2017-06-25 13:12:11 +0800
categories:
- CodeIgniter
- Nginx
---

我平时工作的常用的PHP框架是`CodeIgniter`，它在`Apache`里的配置很简单，根据官方文档设置一下`.htaccess`文件就好了。但`Nginx`上的设置官方文档中没有说明，下面是结合了网上搜索到的方案后，经过自己调试改进后的配置，适配`CodeIgniter` 2和3：

```nginx
server {
    listen       80;

    server_name  example.com;

    set $root '/var/www/example.com';

    root $root;

    index index.php index.html;

    # canonicalize codeigniter url end points
    # if your default controller is something other than "welcome" you should change the following
    if ($request_uri ~* ^(/welcome(/index)?|/index(.php)?)/?$)
    {
        rewrite ^(.*)$ / permanent;
    }

    # removes trailing "index" from all controllers
    if ($request_uri ~* index/?$)
    {
        rewrite ^/(.*)/index/?$ /$1 permanent;
    }

    # removes trailing slashes (prevents SEO duplicate content issues)
    if (!-d $request_filename)
    {
        rewrite ^/(.+)/$ /$1 permanent;
    }

    # removes access to "system" folder, also allows a "System.php" controller
    if ($request_uri ~* ^/system)
    {
        rewrite ^/(.*)$ /index.php?/$1 last;
        break;
    }

    # unless the request is for a valid file (image, js, css, etc.), send to bootstrap
    if (!-e $request_filename)
    {
        rewrite ^/(.*)$ /index.php?/$1 last;
        break;
    }
    
    # fixed post data to json file 405 error
    location ~ (.*\.json)
	{
	    root  $root;
	    error_page 405 =200 $1;
	}

    # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
    #
    location ~ \.php$ {
        fastcgi_pass   127.0.0.1:9000;
        fastcgi_index  index.php;
        fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
        include        fastcgi_params;
    }

    # deny access to apache .htaccess files
    location ~ /\.ht
    {
        deny all;
    }
}
```