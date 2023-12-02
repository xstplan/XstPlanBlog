---
title: Go第二天结构和基础命令和语法
date: 2023-11-26 10:22:39
tags:
- GoLang
---
# **包的概念**
在go语言中包(package)是组织代码的基本单元，用于关联功能在一起，类似C#命名空间（仅次于类似）**一个包可以包含多个源文件**，但这些文件必须要在同一个目录下，并且包名必须相同，每个Go源文件的开头都需要声明所属的包。  
- 包声明在每个go源文件的开头，都需要声明该文件所属的包名
{% codeblock lang:go %}
package main // 声明该文件所属main包
{% endcodeblock %}
- 包的访问权限 Go中的标识符变量或函数名，可以是导出或非导出的。
**导出(大写字母开头，类似C#的public)**
**非导出（小写字母开头，类似C#的private）**
## **入口包**
**main包**：go程序执行入口是**main**包中的“func main()”函数，只有main包可以包含 “func main()”函数。执行程序从这个函数开始。

# **init与main**
## init函数
Init函数是一个特殊的函数，用于在程序运行时候自动执行初始化操作，这个函数在程序开始执行调用，不能显示调用。
- 程序执行前做包的初始化，初始化包的变量
- 一个包可以拥有多个init函数。
- 对于同一个包（同一个源文件或多个源文件组成的包），init() 函数会按照它们在源文件中的编写顺序依次被调用，多个源文件组成一个包，这些文件中的init函数按照文件名排序执行（ASCII字符排序）。
- ini函数不能被其他函数调用，而是在main函数之前，自动被调用
## main函数
**Go语言的默认主函数**
{% codeblock lang:go %}
func main(){

    //函数体
}

{% endcodeblock %}
## init函数和main函数的异同
### 相同点
> 两个函数在定义是不能有任何参数和返回值，都是go程序自动调用。  
### 不同
> **init可以应用任何包中，可以重复定义多个**。  

> **main函数只能用于main包中，只能定义一个**。

# **了解一下go的命令**
输入go之后查看go相关命令（在已经安装的golang环境）
> 
go
Go是一个管理Go源代码的工具。

命令用法：

        go <command> [arguments]

基本command命令:

        bug        启动错误报告
        build      编译包和依赖项
        clean      删除对象文件和缓存文件
        doc        显示包装或符号的文档
        env        打印Go环境信息
        fix        更新包以使用新的API
        fmt        gofmt（重新格式化）包源
        generate   通过处理源生成Go文件
        get        将依赖项添加到当前模块并安装them
        install    编译和安装包和依赖项
        list       列出包或模块
        mod        模块维护
        work       工作空间维护
        run        编译并运行Go程序
        test       测试包
        tool       运行指定的go工具
        version    打印Go版本
        vet        报告包中可能出现的错误

有关命令的详细信息，请使用“go help＜command＞”。

其他帮助主题:

        buildconstraint 生成约束
        buildmode       构建模式
        c               在Go和C之间调用
        cache           构建和测试缓存
        environment     环境变量
        filetype        文件类型
        go.mod          go.mod文件
        gopath          GOPATH环境变量
        gopath-get      传统GOPATH go get
        goproxy         模块代理协议
        importpath      导入路径语法
        modules         模块、模块版本等
        module-get      模块感知go get
        module-auth     使用go.sum的模块身份验证
        packages        程序包列表和模式
        private         下载非公共代码的配置
        testflag        测试标志
        testfunc        测试功能
        vcs             用GOVCS控制版本控制



{% codeblock lang:go %}
package mypackage

var PublicVar int = 10 // 首字母大写的变量，公开的，可以被其他包导入和使用

var privateVar int = 20 // 首字母小写的变量，私有的，只能在当前包内部使用

func PublicFunc() {
    // 这是一个公开的函数，可以被其他包调用
}

func privateFunc() {
    // 这是一个私有的函数，只能在当前包内部使用
}
{% endcodeblock %}
# 基本语法
## **运算符与其他语言相似**

|       运算符    &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;   |          描述        &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;  |
|----|-------------------------------------------------|
| +  | 相加 |
| -  | 相减 |
| /  | 相除 |
| %  | 求余 |

## **关系运算符**

|       运算符    &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;   |          描述        &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;  |
|----|-------------------------------------------------|
| ==  | 检查两个值是否相等，相等True否则返回False |
| !=  | 检查两个值是否不想等，如果不想等返回True否则返回False |
| >  | 检查左边值是否大于右边值，如果是返回True否则返回False |
| >=  | 检查左边值是否大于等于右边值，如果是返回 True 否则返回 False |
| <  | 检查左边值是否小于右边值，如果是返回 True 否则返回 False |
| <=  | 检查左边值是否小于等于右边值，如果是返回 True 否则返回 False |

## **逻辑运算符**
| 运算符 |描述|
|----|-----|
|&&| 逻辑 AND 运算符。 如果两边的操作数都是 True，则为 True，否则为 False|
| \|\| | 逻辑 OR 运算符。 如果两边的操作数有一个 True，则为 True，否则为 False|
|&&| 逻辑 NOT 运算符。 如果条件为 True，则为 False，否则为 True |

## 下划线
“_”下划线是一个特殊标识符，通常作用于占位符和忽略丢弃变量。

- 下划线在import中， **import _ 包路径** 只是用来引用包，仅仅是为了调用init()函数。无法通过包名调用包中的其他函数。
- 下划线在代码中可以表示不需要使用的变量(声明了一个变量但未在后续代码中使用，编译器会提示未使用的变量，并在编译时报错,为了避免这种错误，可以选择使用下划线 _ 来表示这个变量是不使用的)。
## 变量
变量也是与其他语言大差不差，但是声明和使用有所区别。
- **变量声明:** go语言中的变量需要声明之后才能使用，同一个作用于不支持重复声明，**并且变量声明后必须使用**，*否则报错a declared and not used*。
**变量声明为：** 
{% codeblock lang:go %}
var 变量名 变量类型

//基本的变量声明：
var x int // 声明一个变量名为 x，类型为 int，初始值为该类型的零值（0）

//同时声明多个变量
var a, b, c int // 声明多个同类型的变量
var name, age = "Alice", 30 // 初始化同时声明多个变量

var number int // 声明一个变量名为 number，类型为 int，初始值为 0（int 类型的零值）
var isEnabled bool // 声明一个变量名为 isEnabled，类型为 bool，初始值为 false（bool 类型的零值）

//短变量声明（:=）,使用短变量声明可以在函数内部声明并初始化变量，而不需要使用 var 关键字
x := 10 // 声明并初始化一个整型变量 x，类型由编译器自动推断为 int
name, age := "Bob", 25 // 同时声明并初始化多个变量


{% endcodeblock %}
