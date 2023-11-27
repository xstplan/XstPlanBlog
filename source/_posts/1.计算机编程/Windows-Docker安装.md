---
title: Windows-Docker安装
date: 2023-11-27 20:49:21
tags:
- Docker
- 容器
---
# 简单介绍
Docker是一个流行的容器化平台，运行将应用程序和其他所需依赖打包到一个为容器独立单元中，这些容器可以在任何地方运行。
简单来说，Docker就是一个小型虚拟计算机，里面可以包含程序的所需要的一切：代码，运行时，系统工具，库或配置。但是与传统虚拟机不通。容器不需要独立的操作系统，他们是共享主机操作系统的内核，更加轻量级和高效。
# 下载Docker Desktop
Docker Desktop 是 Docker 在 Windows操作系统上的官方安装方式，这个方法依然属于先在虚拟机中安装 Linux 然后再安装 Docker 的方法。
## 安装Hyper-v
``` 控制面板/程序/启动或关闭windows功能/Hyper-V（点击√） ```
## 安装 WSL 2
官方地址：https://learn.microsoft.com/zh-cn/windows/wsl/install

这个呢主要是开发人员可以在 Windows 计算机上同时访问 Windows 和 Linux 。
- 安装子系统
``` 控制面板/程序/启动或关闭windows功能/适用于Linux 的WindowS子系统（点击√） ```

- 在PowerShell输入：``` wsl --list --online ``` 列出可用发行版列表
- 在PowerShell输入： ```wsl.exe --install -d <NAME 名称：如:Ubuntu-22.04>```
- 在PowerShell输入：``` wsl --set-version 命令可用于从 WSL 2 降级到 WSL 1```
- 查看版本：```wsl -l -v```
## 下载
``` https://hub.docker.com/?overlay=onboarding ```

安装完成之后可以输入命令测试：``` docker run hello-world```
