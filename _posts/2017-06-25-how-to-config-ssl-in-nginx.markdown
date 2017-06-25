---
layout: post
title:  如何在Nginx配置SSL？
date:   2017-06-25 13:28:55 +0800
categories:
- Nginx
---

首先需要为域名购买一个`SSL`证书，当然也有不少免费的证书可以申请，但最近各大巨头对于免费的证书封杀得比较厉害，因此不推荐免费的证书。

有了证书后，就可以配置`Nginx`了。

1. 配置`80`端口跳转，把所有`http`访问的链接全部重定向到`https`；

```nginx
server {
   listen 80;
   server_name elrichuang.com www.elrichuang.com;

   rewrite ^(.*)$  https://$host$1 permanent;
}
```

2. 配置`443`端口，因为`https`访问的就是这个端口。

```nginx
server {
   listen 443;
   server_name elrichuang.com www.elrichuang.com;
   ssl on;
   ssl_certificate   /folder_save_ca_keys/xxxxxxxxxxxx.pem; #full path to .pem file
   ssl_certificate_key  /folder_save_ca_keys/xxxxxxxxxxxx.key; #full path to .key file
   ssl_session_timeout 5m;
   ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
   ssl_ciphers AESGCM:ALL:!DH:!EXPORT:!RC4:+HIGH:!MEDIUM:!LOW:!aNULL:!eNULL;
   ssl_prefer_server_ciphers on;

   error_page 497 https://$host&uri?$args; #set error 497 redirect to https

   #other config ...
}
```