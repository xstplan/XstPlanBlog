---
title: Node.js安装与配置环境(Windows版)
date: 2019-01-07 13:11:33
tags: 前端笔记
---

# Nodejs安装
## 下载Node.js
Node.js 官方网站下载：https://nodejs.org/en/download/
![下载](/../Img/20231016195905.png)
## 安装
双击打开安装下一步下一步即可，我默认的路径是 
>C:\Program Files\nodejs

## 查看版本
安装成功之后，运行**cmd** 
输入**node -v**和**npm -v**分别查看node和npm的版本。
# npm安装全局模块的路径和缓存路径
在node.js的安装目录下新建文件夹分别为：
> node_global
> node_cache

创建完成之后在**cmd**中执行命令

```npm config set prefix "C:\Program Files\nodejs\node_global"```

```npm config set cache "C:\Program Files\nodejs\node_cache"```

**设置完成之后进行环境变量的配置分别为:**

``` “环境变量”>“系统变量”：新建一个变量名为“NODE_PATH”，值为“D:\Program Files\nodejs\node_global\node_modules”```

``` “环境变量”>“用户变量”：编辑用户变量里的path，相应npm的路径C:\Users\用户名\AppData\Roaming\npm```

```“环境变量”>“用户变量”：编辑用户变量里的path，相应npm的路径C:\Program Files\nodejs\node_global```

配置完成之后，测试npm下载即可。
