---
title: .Net扩展、库、工具、持续更新
date: 2023-12-2 14:00:40
categories: 后端笔记
tags: 
- C#
- .Net Core
---
# 库与框架
## .Net系统框架
### Avalonia - 跨平台 UI 框架
> Avalonia是 dotnet 的跨平台 UI 框架，提供灵活的样式系统，支持 Windows、macOS、Linux、iOS、Android 和 WebAssembly 等多种平台。

### Ant Design of Blazor 
> Blazor样板的企业应用程序的开箱即用 UI 解决方案

## 容器注入

### Autofac
> Autofac是一个用于依赖注入（DI）和反转控制（IoC）的.NET库，提供了一个容器，用于注册、解析和管理应用程序中的组件，这些组件包括服务、对象和其他依赖项。


### Prism - 框架库
> Prism 是一个框架，用于在 WPF 和 Xamarin Forms 中构建松散耦合、可维护和可测试的 XAML 应用程序。每个平台都有单独的版本，并且这些版本将按照独立的时间表进行开发。Prism 提供了一系列设计模式的实现，这些设计模式有助于编写结构良好且可维护的 XAML 应用程序，包括 MVVM、依赖项注入、命令、EventAggregator 等。


### CommunityToolkit.MVVM - MVVM 工具包
> CommunityToolkit.MVVM是一个用于创建基于MVVM（Model-View-ViewModel）设计模式的应用程序的开源工具包，它是Microsoft的CommunityToolkit项目的一部分。这个工具包旨在帮助开发人员更容易地构建XAML应用程序。

## 图表
### LiveCharts2 - 实时图表
> LiveCharts 是一个.Net 数据可视化库，可以跨多个设备和框架运行。包含MAUI，AVALONIA，UNO PLATFORM， ETOFOROMS，XAMARIN，BLAZOR WASM，WPF。
### SparrowToolkit 
> 一套WPF图表控件集，支持绘制动态曲线，可绘制示波器、CPU使用率和波形。
## 文档操作
### iTextSharp
> iTextSharp是一个用于生成和操作PDF文档的C#库。它允许开发人员创建、读取、修改和分析PDF
### QuestPDF - 生成 PDF 文档的现代开源 .NET 库
> QuestPDF 是一个用于生成 PDF 文档的现代开源 .NET 库。它支持所有 .NET 平台，包括 .NET Framework、.

### HtmlAgilityPack - 爬虫库
> HtmlAgilityPack是一个基于.Net的、第三方免费开源的微型类库,主要用于在服务器端解析html文档。

### NPOI - 工具库
> 一个用于操作Microsoft Office文件格式的开源库。它允许开发人员在.NET平台上创建、读取和编辑Microsoft Excel（.xls和.xlsx）、Word和PowerPoint等文件格式。NPOI 提供了一种方便的方式来处理Office文档，以便在应用程序中进行数据导入、导出、报表生成等操作。

## 通讯
### SignalR - 通讯库
> SignalR 是一个开源的.NET库，用于在实时应用程序中实现双向通信。它允许开发人员构建具有实时功能的应用程序，例如聊天应用、在线游戏、协作工具、股票市场更新、监控系统等。

## 任务调度框架
### Quartz.Net - 任务调度框架
> 用于构建作业调度应用程序的.NET库。它支持多种存储类型，包括关系数据库、文件、MSMQ、RavenDB、SQLServer、Oracle、MySQL、PostgreSQL、SQLite、NoSQL等。
### Hangfire - 任务调度框架
> Hangfire 是一个开源的.NET库，用于在后台执行任务调度。
### Topshelf
> Topshelf 是一个开源的.NET库，用于构建Windows服务。它提供了一个简单的API，用于定义、安装和运行.NETWindows服务。

## 分布式缓存框架
### StackExchange.Redis - 分布式缓存框架
> 用于构建分布式缓存系统的.NET客户端库。它支持Redis、Memcached、Couchbase和MongoDB等缓存系统
### Memcahed -  分布式缓存框架
> Memcached 是一个高性能、分布式内存对象缓存系统，用于动态Web应用以减轻数据库负载。

## 中间件与消息队列
### RabbitMQ
> 基于 AMQP 协议，RabbitMQ 是一个开源的，由 Erlang 语言编写的，面向消息的中间件。
### Redis 
> Redis 是一个开源的、内存中的数据结构存储系统，它可以用作数据库、缓存和消息中间件。
### Kafka/Jafka
> Kafka是Apache下的一个子项目，是一个高性能跨语言分布式发布/订阅消息队列系统，而Jafka是在Kafka之上孵化而来的，即Kafka的一个升级版。
## 常用ORM框架
### Dapper - 轻量级ORM框架
> Dapper 是一个轻量级的ORM框架，它允许开发人员通过简单、一致和类型安全的API来访问数据库。
### NHibernate - ORM框架
> NHibernate 是一个开源的对象关系映射（ORM）框架，它允许开发人员使用面向对象的模型来操作关系数据库。
### EntityFramework - ORM框架
> 微软的Entity Framework 是一个对象关系映射（ORM）框架，它允许开发人员使用面向对象的模型来操作关系数据库。
### SqlSugar - ORM框架
SqlSugar 是一款老牌.NET 开源多库架构ORM框架（EF Core单库架构），由果糖大数据科技团队. 维护和更新。
### SubSonic - ORM框架
> SubSonic 是一个开源的.NET ORM框架，它允许开发人员使用面向对象的模型来操作关系数据库。
# 第三方接口库
### DotNetCore.SKIT.FlurlHttpClient.Wechat -  微信接口库
> 微信开放平台API接口封装库，支持微信公众号、小程序、企业号、企业微信、微信支付、开放平台、企业内部系统对接。

# WPF UI库
### MaterialDesignThemes.Wpf
### HandyControl 
### MahApps.Metro 
### Fluent.Ribbon - 像 Office 中一样的 WPF 功能区控件
### WPF UI - WPF是用于构建桌面应用程序的.NET框架。
# 扩展
- **XAML Styler:** XAML 格式化（  (?<=\r\n)\r\n  ）
- **ResXManager:** 使用基于 resx 的资源本地化和管理各种应用程序的最流行工具。显示解决方案的所有资源，让您在排列良好的数据网格中编辑字符串及其本地化。
- **Codemaid:** 一个开源 Visual Studio 扩展，用于清理和简化 C#、C++、F#、VB、PHP、PowerShell、R、JSON、XAML、XML、ASP、HTML、CSS、LESS、SCSS、JavaScript 和 TypeScript 编码。


