---
title: Go第三天Array和Slice
date: 2023-12-02 13:06:54
tags:
- GoLang
---
# 数组
- 数组是一种数据类型固定长度的序列。
- 数组定义：var a [长度] int，数组长度是一个常量，类型的组成部分。一旦定义，长度就不能变了。
> Go中的数组是值类型，当数组传递到函数时，会进行值复制，因此对函数内部的数组进行修改不会影响原始数组。

{% codeblock lang:go %}
var arr [5]int //声明一个包含5个整数的数组

arr:=[3]int{10,20,30}//初始化数组并指定初始值

arr:=[0]=100//修改数组的第一个元素为100
value:=arr[1]//获取数组的第二个元素值

length:=len(arr)//获取数组长度

var mat[3][3]int //声明一个3x3的二维整数数组
{% endcodeblock %}

# slice 切片
在大多数情况下，Go更倾向于使用切片，因为切片具有动态长度且更有灵活，长度不固定，切片是对数组的抽象，切片的长度可以动态增长和缩减。
{% codeblock lang:go %}
var slice []int //声明一个整数切片，初始化为null

slice:=[]int{10,20,30}//初始化切片指定默认值

slice := arr[1:4] // 创建一个包含 arr 数组索引为 1 到 3 的切片

slice := arr[2:] // 从索引为 2 的元素开始直到末尾
slice := arr[:3] // 从开始到索引为 2 的元素（不包含索引为 3 的元素）
slice := arr[:] // 完整拷贝整个数组

slice = append(slice, 6) // 在切片末尾追加一个元素
slice = append(slice, 7, 8, 9) // 在切片末尾追加多个元素

slice = append(slice, 10) // 当容量不足时，切片会自动扩容

length := len(slice) // 获取切片的长度
capacity := cap(slice) // 获取切片的容量
{% endcodeblock %}
> 在 Go 中，切片的扩容是指在切片容量不足以容纳新添加元素时，系统会自动为切片分配更多的内存空间，使其能够容纳更多的元素。
## 使用make创建切片

make用于创建动态长度的数据结构，切片、或者映射、通道等内建函数。

{% codeblock lang:go %}
slice := make([]int, 5) // 创建一个包含5个整数的切片，初始值为整数类型的零值
slice := make([]int, 5, 10) // 创建一个长度为5，容量为10的切片


{% endcodeblock %}


>  总结：数组适合于固定长度、静态集合的场景，而切片则更适用于需要动态改变长度、灵活操作数据集合的情况。