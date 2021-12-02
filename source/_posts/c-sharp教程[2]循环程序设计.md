---
title: 'C#教程[2] 循环程序设计'
tag:
  - c#
categories:
  - 电子电路社
  - c#教程
mathjax: false
abbrlink: 3965
date: 2021-11-29 00:00:00
---

{% note warning flat %}
本文未完工
{% endnote %}

之前学的程序里的语句都只能执行最多一次, 无法发挥出计算机的优势. 而为了让代码中的一行语句可以被执行若干遍, 于是, 便有了循环.

# `while` 循环

假设我们要写一个程序永远不停的输出 `hello world` (直到你关掉它), 代码如下:

```csharp
while(true)
{
	Console.WriteLine("hello world");    
}
```

其中小括号里的为条件, 大括号里的(即这个代码块)为参与循环的部分

{% note warning flat %}
不能写成 `while(1)`, 当你学习完下一章数据类型转换的时候你会对此有更深的感悟
{% endnote %}

# `for`循环

```csharp
for (int i=0; i < 10; i++)
{
  Console.WriteLine("i的值为: {0}", i);
}
```

# 练习
## 2-1 阶乘  (P5739 【深基7.例7】计算阶乘)
输入 `n`, 输出 `n` 的阶乘(n <= 12)

## 2-2 aabb
输出所有形如 `aabb` 的完全平方数

参考程序:
```csharp
using System;

for(int i=1; ; i++)
{
    int n = i * i;
    if (n < 1000) continue;
    if (n > 9999) break;

    int aa = n / 100; // 取前2位数字
    int bb = n % 100; // 取后2位数字
    if (aa / 10 == aa % 10 && bb / 10 == bb % 10) Console.WriteLine(n);
}
``` 