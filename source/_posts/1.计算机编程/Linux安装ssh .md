---
title: Linux安装ssh 
date: 2023-11-25 15:00:00
tags: 
- Linux
---
# 安装ssh
```
sudo apt-get install openssh-server
```

如果出现错误 **暂时不能解析域名“cn.archive.ubuntu.com** 错误，重新启动网络。

# 启动ssh服务
```
sudo service ssh start
```

# 连接

ssh [用户名]@192.168.13.00