---
title: Git常见错误
date: 2023-12-23 10:00:00
categories: Git常见错误
tags: 
- Git
- 错误
---


#### Failed to connect to github.com port 443 after ***** ms: Couldn‘t connect to server
> 解决方法:设置---网络和Internet---代理---地址:端口  

![](../../Img/2023122311111.png)

修改git配置:
{% codeblock lang:powershell %}
git config --global http.proxy http://127.0.0.1:4780
git config --global https.proxy http://127.0.0.1:4780
{% endcodeblock %}
再执行**git clone**即可

如果不行则取消代理
git config --global --unset http.proxy

git config --global --unset https.proxy