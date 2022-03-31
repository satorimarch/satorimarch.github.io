---
title: 'C#中的数据类型转换'
tags:
  - c#
categories:
  - 电子电路社
  - c#教程
cover: 'https://s6.jpg.cm/2021/11/28/LLOoFu.png'
abbrlink: 19004
date: 2021-08-19 00:00:00
---

C# 是一门强类型语言，对类型的要求很严格，类型转换的方式有两种：**隐式类型转换**和**显式类型转换**。

# 隐式类型转换

```csharp
int a = 5;
double b = 1.5;
double c = a + b;
System.Console.WriteLine(c);
```

像这样，并没有在源代码里进行任何特殊处理，而是由编译器自动进行了从`int`类型到`double`类型的隐式转换。

但是很多类型之间不可以进行隐式类型转换，可以看下面的例子。

```csharp
int a = 1.5;
Console.WriteLine(a);
```

在作者的电脑上编译时会有这样的报错：

> error CS0266: 无法将类型“double”隐式转换为“int”。存在一个显式转换(是否缺少强制转换?)

因此，我们需要用显式类型转换改正它。

# 显式类型转换

上面的例子的第一行应改为这样：

```csharp
int a = (int)1.5;
```

语法就是在要转换的变量前加一组小括号，里面写要转换成的类型名。所有的隐式类型转换都可以写成显式。

但是这样写输出的结果却是`1`而非四舍五入的`2`

用显式类型转换**会丢失数据的精度**，这也是为什么不会自动进行显式类型转换。显式类型转换又叫强制类型转换。

而且显式类型转换也并非所有类型之间都能转的，例如下面这么写也是**错误**的：

```csharp
double a = (double)"5.5";
```

{% note warning %}
在许多其他编程语言里，`int`可以隐式转换为`bool`，但是 C# 中无论是隐式还是显式都会报错，要使用后面提到的`Convert.ToBoolean()`
{% endnote %}

为了解决上述的问题，我们将介绍使用方法进行类型转换。

# 使用方法进行类型转换

## 使用`ToString()`方法

所有的类型都可以使用`ToString()`方法（因为 `Object` 类定义了 `ToString` 方法，而所有类都直接或者间接派生自 `Object` 类），如下：

```csharp
int a = 5;
string b = a.ToString();
```

## 使用`Convert.ToInt32()`方法

`Convert`类提供了许多转换的方法，例如：`ToChar()`，`ToDouble()`，`ToBoolean()` 甚至 `ToDateTime()`

```csharp
int a = Convert.ToInt32("55");
double b = Convert.ToDouble("5.5");
string s = Convert.ToString(123);
```

## 使用`Type.Parse(string)`方法

`Parse()`方法用来将**字符串**转换为其他的**数值**类型

{% note warning %}
`Parse()` 方法的参数只能是字符串
而 `Type` 只能是数字类型
{% endnote %}


使用时 `类型名.Parse(需要转换的变量);` 即可

例如：

```csharp
string a = "5";
int b = int.Parse(a);
```

## 注意事项：

1. 试图将字符串`"5.5"`转换成`int`类型时，下面两种方法都是**错误**的：

```csharp
int a = Convert.ToInt32("5.5");
int a = int.Parse("5.5");
```

正确的做法应该是先把字符串 `"5.5"` 转换成 `double` 类型，再转换成 `int` 类型：

```csharp
int a = (int)Convert.ToDouble("5.5");
int a = (int)Double.Parse("5.5");
```

2. 进行从字符串到数值类型转换时 `Convert` 和 `Parse` 做法一般可以互换, 区别在于对 `null` 的处理不同:
```csharp
int a = Convert.ToInt32(null); // a == 0
int b = int.Parse(null); // 异常
```

3. 如果您希望自己封装的类可以被 `Convert` 类转换为基本类型, 请继承`IConvertible` 接口, 如果你觉得有些类型不应该被转化(点名`ToDateTime`), 请抛出 `InvalidCastException` 异常

另外, 传入空字符串 `""` 时两者都会抛出异常

## 使用 `int.TryParse()` 方法

微软官方教程中的说明如下：

> `TryParse()` 方法可同时执行多项操作：
>
> 1. 它会**尝试**将字符串分析成给定的数字数据类型。
>
> 2. 如果成功，它会将转换后的值存储在 **out 参数**中。
>
> 3. 它会**返回布尔值**来指示操作是否成功。
>
> 对于**所有数字数据类型**，均可使用类似的 `TryParse()` 方法。

例如：

```csharp
double result;
bool a = double.TryParse("5.5", out result); // result 即为说明中第2条的 "out参数" 
Console.WriteLine($"a = {a}");  // c#6.0 以上才能用字符串内插
Console.WriteLine($"result = {result}");
```

此时，输出结果应为：

```csharp
a = True
result = 5.5
```

`out` 关键字的用法类似 `ref` 关键字, 本质上都是传入引用, 且都需要在方法的定义和调用时显式使用该关键字

主要的区别为:
1. 使用 `ref` 必须在传参之前进行显式的初始化, 而 `out` 有没有都行
2. 离开方法之前必须对有 `out` 关键字的参数赋值(否则通不过编译)
3. 使用 `out` 的参数在方法中被视为未被初始化的
4. 尽管你可以给传入赋值过的变量, 但在传入时参数的值是没有意义的

另外, `out` 其实就是用 `ref` 来实现的, 所以不可以像 `Func(ref int a)` `Func(out int a)` 这样重载

### 示例（来自微软官方文档 [链接](https://docs.microsoft.com/zh-cn/learn/modules/csharp-convert-cast/4-challenge)）

已知一个字符串数组 `values`

```csharp
string[] values = { "12.3", "45", "ABC", "11", "DEF" };
```

循环访问字符串数组中的每个值：如果值是字母，则连接它以形成消息；如果值是数字，则将其加到总计值


输出：
{% note default %}
Message: ABCDEF
Total: 68.3
{% endnote %}

示例代码:

```csharp
using System;

string[] values = { "12.3", "45", "ABC", "11", "DEF" };

double total = 0.0;
string message = "";

foreach (string v in values)
{
    if (decimal.TryParse(v, out double temp)) total += temp;
    else message += v; 
}

Console.WriteLine($"Messagae: {message}");
Console.WriteLine($"Total: {total}");
```
