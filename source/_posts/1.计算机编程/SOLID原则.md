---
title: SOLID原则
date: 2019-10-20 09:00:36
categories: 设计原则
tags: 
- 设计原则
- 面向对象
---
# SOLID原则
## 什么是SOLID

首先SOLOD原则就是一组面向对象编程的设计原则，主要作用是改善软件设计、提高代码质量，增加软件的可维护性和可扩展性。

SOLID相应代表：
- **S 单一职责原则(Single Responsibility Principle)**
- **O 开放封闭原则(Open/Closed Principle)**
- **L 里氏替换原则(Liskov Substiution Principle)**
- **O 接口隔离原则(Interface Segregation Principle)**
- **D 依赖反转原则(Dependencey Inversion Principle)**

## 单一职责原则
单一职责原则主要介绍一个类的责任应该是单一的，它应该只有一个理由去来改变，类里的方法或属性应该与责任有关。每个类都有清晰的目标和职责。

>简单来说让一个程序员去打代码，还要让设计海报，工作变得复杂，容易出错。那么我们要根据单一职责，以确保每项任务得到专业的处理，打代码的就是来代码，设计海报的就来设计海报。
也可以理解为游戏中的法师、战士、辅助。他们都有特定的任务职责。

### 违反单一职责的示例

{% codeblock lang:C# %}
/// <summary>
/// 文件处理类
/// </summary>
public class FileProcessor
{
    public string ReadFile(string filePath)
    {
        // 读取文件的具体实现
    }

    public int CountCharacters(string text)
    {
        // 统计字符数的具体实现
    }
}

{% endcodeblock %}

### 遵循单一职责的示例


{% codeblock lang:C# %}
 
public class FileReader
{
    public string ReadFile(string filePath)
    {
        // 读取文件的具体实现
    }
}

public class CharacterCounter
{
    public int CountCharacters(string text)
    {
        // 统计字符数的具体实现
    }
}

{% endcodeblock %}
## 开放封闭原则
开放封闭原则主要强调软件实体、类、模块、函数应该对扩展开放，对修改封闭。这意味着添加新的功能或者更改现有功能时，不应该修改已经存在的代码，而是应该通关扩展现有代码来实现。

> 一旦写好一段代码，就不要再去修改他，相反如果添加新的功能，不要动原来的代码，而是在基础之上添加新的东西。如果在修改原来的代码可能会导致原来的功能变的不稳定。通过新的东西，可以确保旧的功能保持不变。

### 违反开放封闭原则的示例

一个图形绘制应用程序，后面添加新需求要求添加一个新的形状。
{% codeblock lang:C# %}
public class Rectangle
{
    public double Width { get; set; }
    public double Height { get; set; }
}

public class AreaCalculator
{
    public double CalculateArea(object shape)
    {
        if (shape is Rectangle)
        {
            var rectangle = (Rectangle)shape;
            return rectangle.Width * rectangle.Height;
        }
        // 现在需要添加一个新的形状（例如圆形）的计算，就需要修改这个类。
        // 这违反了开放封闭原则。
        else if (shape is Circle)
        {
            var circle = (Circle)shape;
            return Math.PI * Math.Pow(circle.Radius, 2);
        }
        return 0;
    }
}

{% endcodeblock %}

### 遵循开放封闭原则的示例
以下代码我们抽象类一个Shape类，定义了一个抽象方法，并有两个子类，每个类负责实现自己的计算面积方法。

{% codeblock lang:C# %}
public abstroct class Shape
{
  public abstract double CalculateArea();

}

public class Rectangle : Shape
{
    public double Width { get; set; }
    public double Height { get; set; }

    public override double CalculateArea()
    {
        return Width * Height;
    }
}

public class Circle : Shape
{
    public double Radius { get; set; }

    public override double CalculateArea()
    {
        return Math.PI * Math.Pow(Radius, 2);
    }
}
{% endcodeblock %}
## 里氏替换原则
里氏替换原则强调在面向对象中，子类应该能够替换其基类而不引起不一致或错误。如果一个类型是基类，那么它的子类应该可以无缝地替代它。
- 子类必须保持基类的行为
- 子类可以扩展基类的功能
- 子类不应该引入新的错误
- 子类不应该强制基类行为
### 违背里氏替换原则的示例：
假设我们有一个基类 Bird 表示鸟类，它有一个 Fly 方法用于飞翔。
{% codeblock lang:C# %}
public class Bird
{
    public void Fly()
    {
        Console.WriteLine("这只鸟在飞翔");
    }
}

{% endcodeblock %}
然后，我们创建了一个子类 Penguin 表示企鹅。企鹅是一种鸟，但它不会飞翔。
{% codeblock lang:C# %}
public class Penguin : Bird
{
    // 企鹅不能飞，但我们仍然继承了父类的 Fly 方法，这违背了里氏替换原则。
}
{% endcodeblock %}

### 遵守里氏替换原则的示例：
为了遵守里氏替换原则，我们创建一个接口 IFlyable 表示可以飞翔的行为，然后只有能够飞翔的鸟类实现这个接口。

{% codeblock lang:C# %}
public interface IFlyable
{
    void Fly();
}

public class Bird : IFlyable
{
    public void Fly()
    {
        Console.WriteLine("这只鸟在飞翔");
    }
}

public class Eagle : IFlyable
{
    public void Fly()
    {
        Console.WriteLine("这只鹰在飞翔");
    }
}
{% endcodeblock %}

## 接口分离原则 
接口分离原则强调一个类不应该强制实现它用不到的接口。
- 接口应该小，不应该包含过多的方法
- 类应该只实现与关系密切的接口，避免实现不相关方法
- 如果一个接口变得很庞大，应该拆分成小接口
### 违背接口分离的示例
{% codeblock lang:C# %}

public interface IMultiFunctionDevice
{
    void Print();
    void Scan();
    void Copy();
}
//打印机不需要扫描和复印
public class AllInOnePrinter : IMultiFunctionDevice
{
    public void Print()
    {
        // 打印操作
    }

    public void Scan()
    {
        // 不需要扫描，但还是要实现
    }

    public void Copy()
    {
        // 不需要复印，但还是要实现
    }
}
{% endcodeblock %}
### 遵循接口分离的示例
AllInOnePrinter 类只需要实现 IPrinter 接口，而不需要实现不相关的方法。
{% codeblock lang:C# %}

ppublic interface IPrinter
{
    void Print();
}

public interface IScanner
{
    void Scan();
}

public interface ICopier
{
    void Copy();
}

public class AllInOnePrinter : IPrinter
{
    public void Print()
    {
        // 打印操作
    }
}

{% endcodeblock %}


## 依赖反转原则
依赖反转主要强调高层模块**不要直接**依赖底层模块，二者都需要依赖于抽象，具体细节不应该依赖抽象，而抽象应该依赖于具体细节。
- 高层模块不应该直接依赖底层模块，他们直接要依赖于抽象。
- 抽象不依赖于具体，具体应该依赖于抽象
如抽象层，(接口或者抽象类)，以定义高层模块和底层模块之间的通信接口。高层模块依赖于抽象，而具体的底层模块实现这些抽象。
### 违背依赖反转的示例
Driver类直接依赖于具体的车型，DriveElectricCar和DriveGasolineCar方法分别依赖于ElectricCar和GasolineCar。这违反了依赖反转，因为高层模块（Driver）直接依赖于低层模块（ElectricCar和GasolineCar）。
{% codeblock lang:C# %}
public class ElectricCar
{
    public void Drive()
    {
        // 电动车行驶逻辑
    }
}

public class GasolineCar
{
    public void Drive()
    {
        // 内燃机车行驶逻辑
    }
}

public class Driver
{
    public void DriveElectricCar(ElectricCar car)
    {
        car.Drive();
    }

    public void DriveGasolineCar(GasolineCar car)
    {
        car.Drive();
    }
}
{% endcodeblock %}
### 遵守依赖反转的示例

{% codeblock lang:C# %}
public interface ICar
{
    void Drive();
}
引入一个抽象的Car接口，然后让具体的车型实现它。Driver类不再依赖于具体的车型，而是依赖于抽象的Car接口：
public class ElectricCar : ICar
{
    public void Drive()
    {
        // 电动车行驶逻辑
    }
}

public class GasolineCar : ICar
{
    public void Drive()
    {
        // 内燃机车行驶逻辑
    }
}

public class Driver
{
    public void DriveCar(ICar car)
    {
        car.Drive();
    }
}
{% endcodeblock %}