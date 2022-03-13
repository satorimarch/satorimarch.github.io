---
title: 'C#教程[6] 面向对象'
tag:
  - c#
categories:
  - 电子电路社
  - c#教程
mathjax: true
abbrlink: d4ed487
date: 2022-02-04 00:00:00
---

{% note danger flat %}
本文未完工
{% endnote %}

# 类(Class)和对象(object)

之前的教程里已经大量渗透了与类型(Type)和对象有关的概念, 但我们还没有正式介绍过什么是类(Class)

类是对事物的一种抽象定义, 就是一类对象的统称, 是一类对象共有的属性和行为

再回过头来看对象的定义: 对象是类的具体实现，表示一个独立的、唯一的个体。

举个现实世界的例子, 猫这类动物就是一个类, Cat类有很多共有的属性：颜色、名字、品种, 也有很多共有的行为：叫、吃东西等。而你特指的某一只猫就是Cat类的对象。

{% note info flat %}
对象是类的实例，类是对象的抽象
{% endnote %}

我们以前 `new` 一个对象的时候其实就是创建了这个类的实例, 例如之前我们用过的 `Random` 类:
```csharp
Random rd = new Random();
```

定义一个类的语法如下(应与Program类并列):
```csharp
class Student
{
    public string name; // 定义成员变量
    public int age;
    public int height;
    public int weight;
}
```

然后你可以在 `Main` 方法中创建 `Student` 类的实例:

```csharp
class Student
{
    public string name;
    public int age;
    public int height;
    public int weight;
}

class Program
{
    static void Main(string[] args)
    {
        Student student1 = new Student();
        student1.name = "xiaoming";

        Console.WriteLine(student1.name);
    }
}
```

# 构造函数

还记得第三节里DataTime类的构造函数吗 
例如:
```csharp
DataTime dt = new DateTime(1919, 8, 10, 11, 45, 14);
```

# 类的封装

## 访问修饰符

## 属性(Property)

# 类的继承

# 类的多态