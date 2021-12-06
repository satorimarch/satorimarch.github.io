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

像这样，并没有对源代码进行任何特殊处理，而是由编译器自动进行了从`int`类型到`double`类型的隐式转换。

但是很多类型之间不可以进行隐式类型转换，可以看下面的例子。

```csharp
double a = 1.5;
int b = a;
System.Console.WriteLine(b);
```

在作者的电脑上编译时会有这样的报错：

> 错误	CS0266	无法将类型“double”隐式转换为“int”

因此，我们需要用显式类型转换改正它。

# 显式类型转换

上面的例子的第二行应改为这样：

```csharp
int b = (int)a;
```

语法就是在要转换的变量前加一组小括号，里面写要转换成的类型名。所有的隐式类型转换都可以写成显式。

但是这样写输出的结果却是`1`而非想象中的四舍五入`2`。

用显式类型转换**会丢失数据的精度**，这也是为什么编译器不会自动进行显式类型转换。显式类型转换又叫强制类型转换。

而且显式类型转换也并非所有类型之间都能转的，例如下面这么写也是**错误**的：

```csharp
double a = (double)"5.5";
```

**注意：**在许多其他编程语言里，`int`可以隐式转换为`bool`，但是C# 中无论是隐式还是显式都会报错，要使用后面提到的`Convert.ToBoolean()`

为了解决上述的问题，我们将介绍使用方法进行类型转换。

# 使用方法进行类型转换

## 使用`ToString()`方法

所有的类型都可以使用`ToString()`方法，如下：

```csharp
int a = 5;
string b = a.ToString();
```

## 使用`Convert.ToInt32()`方法

`Convert`为类名，`ToInt32()`为其中的方法名。`Convert`类提供了许多转换的方法，例如：`ToChar()`，`ToDouble()`，`ToBoolean()`

例如：

```csharp
int a = Convert.ToInt32("5.0");
```

## 使用`int.Parse()`方法

`Parse()`方法用来将**字符串**转换为其他的类型

### 注意：`Parse()`方法的参数只能是字符串

使用时 `类型名.Parse(需要转换的变量);`  即可

例如：

```csharp
string a = "5";
int b = int.Parse(a);
```

虽然例子中用的是`int`类型，但实际上所有数字类型都有类似的方法。

但是将字符串`"apple"`转换为int时还是会报错导致程序无法继续运行，且我们也并不真的希望他把`apple`转为`int`类型，这时我们可以使用`TryParse()`方法。

## 使用 `int.TryParse()`等方法

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
string str = "5.5";
bool a = double.TryParse(str, out result); // result 即为说明中第2条的 "out参数" 
System.Console.WriteLine($"a = {a}\nresult = {result}\n");
```

此时，输出结果应为：

```csharp
a = True
result = 5.5
```

## 例题：（来自微软官方文档 [链接](https://docs.microsoft.com/zh-cn/learn/modules/csharp-convert-cast/4-challenge)）

### 题意：

已知一个字符串数组`values`

```csharp
string[] values = { "12.3", "45", "ABC", "11", "DEF" };
```

循环访问字符串数组中的每个值， 对于每个值满足以下规则：

规则 1：如果值是字母，则连接它以形成消息

规则 2：如果值是数字，则将其加到总计值

### 样例输出：

```csharp
Message: ABCDEF
Total: 68.3
```

### 示例代码:

官方:

```csharp
using System;

string[] values = { "12.3", "45", "ABC", "11", "DEF" };

decimal total = 0m;
string message = "";

foreach (var value in values)
{
    decimal number;
    if (decimal.TryParse(value, out number))
    {
        total += number;
    } else
    {
        message += value;
    }
}

Console.WriteLine($"Message: {message}");
Console.WriteLine($"Total: {total}");
```
作者的版本:

```csharp
using System;

string[] values = { "12.3", "45", "ABC", "11", "DEF" };

decimal total = 0.0m;
string message = "";

foreach (string v in values)
{
    if (decimal.TryParse(v, out decimal curr)) total += curr; // 这样写curr变量只会在if语句的范围内生效
    else message += v; 
}

Console.WriteLine($"Messagae: {message}\nTotal: {total}\n");

```

## 其他注意事项：

试图将字符串`"5.5"`转换成`int`类型时，下面两种方法都是**错误**的：

```csharp
int a = Convert.ToInt32("5.5");
int a = int.Parse("5.5");
```

正确的做法应该是先**把字符串`"5.5"`先转换成`double`类型，再转换成`int`类型**，比如下面两种方法：

```csharp
int a = (int)Convert.ToDouble("5.5");
int a = (int)Double.Parse("5.5");
```

