---
title: 'C#教程[3] 循环程序设计'
tag:
  - c#
categories:
  - 电子电路社
  - c#教程
mathjax: false
abbrlink: 3965
date: 2021-11-29 00:00:00
---

{% note danger flat %}
本文未完工
{% endnote %}

之前学的程序里的语句都只能执行最多一次, 无法发挥出计算机的优势. 而为了让代码中的一行语句可以被执行若干遍, 于是便有了循环.

# `while` 循环

假设我们要写一个程序永远不停的输出 `hello world` (直到你关掉这个程序), 代码如下:

```csharp
while(true)
{
	Console.WriteLine("hello world");    
}
```

其中小括号里的为条件, 大括号里的(即这个代码块)为参与循环的部分

{% note warning flat %}
不能写成 `while(1)`, 当你了解了 `C#` 中的数据类型转换机制的时候你会对此有更深的感悟
{% endnote %}

# `for` 循环

以下代码列是一个简单的 `for` 语句，它循环遍历其代码块（即被大括号括起来的内容）十次，并打印 `i` 的当前值。

```csharp
for (int i=0; i < 10; i++)
{
  Console.WriteLine("i的值为: {0}", i);
}
```

## 例题 3-1
FizzBuzz 问题:

 - 每行一个数字 输出值 1 到 100。
 - 如果当前值可被 3 整除，则在该数字旁打印 Fizz。
 - 如果当前值可被 5 整除，则在该数字旁打印 Buzz。
 - 如果当前值可 同时 被 3 和 5 整除，则在该数字旁打印 FizzBuzz。

例如:
```
1
2       
3 - Fizz
4       
5 - Buzz
6 - Fizz
7       
8
9 - Fizz
10 - Buzz
11
12 - Fizz
13
14
15 - FizzBuzz
```

示例程序：
```csharp
for(int i=1; i <= 100; i++){
    if(i % 3 == 0 && i % 5 == 0) {
        Console.WriteLine("{0} - FizzBuzz", i);
    }
    else if(i % 3 == 0) {
        Console.WriteLine("{0} - Fizz", i);
    }
    else if(i % 5 == 0) {
        Console.WriteLine("{0} - Buzz", i);
    }
    else {
        Console.WriteLine(i);
    }
}
```


# 练习
## 3-1 阶乘  (P5739 【深基7.例7】计算阶乘)
输入 `n`, 输出 `n` 的阶乘(n <= 12)

## 3-2 aabb
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