---
title: 'C#教程[2] 循环程序设计'
tag:
  - c#
categories:
  - 电子电路社
  - c#教程
sticky: 1
mathjax: true
abbrlink: 3965
date: 2021-11-29 00:00:00
---

之前学的程序里的语句都只能执行最多一次, 无法发挥出计算机的优势. 而为了让代码中的一行语句可以被执行若干遍, 于是便有了循环.

# 循环语句

## `while` 循环

假设我们要写一个程序永远不停的输出 `hello world` (直到你关掉这个程序), 代码如下:

```csharp
while (true) {
	Console.WriteLine("hello world");    
}
```

其中小括号里的为条件, 大括号里的(即这个代码块)为参与循环的部分
在进入循环之前会先判断括号里的条件，如果为 `true` 才执行，每次执行完大括号里的内容会再次判断括号里的条件，如果为 `true` 则再次执行大括号里的内容，循环往复直到括号里的条件为 `false`

因为上面的例子中括号里恒为 `true` 所以这个循环会永远进行下去

{% note warning flat %}
不能写成 `while(1)`, 当你了解了 `C#` 中的数据类型转换机制的时候你会对此有更深的感悟
{% endnote %}

再举一个不是死循环的例子：

```csharp
int a = 5;
while (a < 10) {
    Console.WriteLine("a 的值： {0}", a);
    a++; // 自增运算符, 相当于 a = a + 1;
}
```

大家可以预测一下输出的结果。

{% hideToggle 点我查看输出结果 %}

```
a 的值： 5
a 的值： 6
a 的值： 7
a 的值： 8
a 的值： 9
```

{% endhideToggle %}

### 猜数游戏

在这里先介绍一下如何生成随机数：

```csharp
Random rd = new Random(); // 如果要生成多组随机数 这行也只需要在最开始写一遍
int a = rd.Next(); // Next()函数返回下一个随机数
```

这么写具体的原理会在下一节进行解释

如果要生成指定范围内的随机数应该写为：

```csharp
rd.Next(5, 11); // 左闭右开，所以此处为 [5,11) 范围内的随机数，并不包括 11
```

这样我们就可以写一个猜数游戏了：生成 [1,100] 内的一个随机数，让玩家来猜这个数的大小，提示玩家猜测的数是偏大还是偏小，直到玩家猜中

代码：

```csharp
Random rd = new Random();
int a = rd.Next(1, 101);

Console.WriteLine("");
Console.WriteLine("输入你猜测的数字:");

int num = Convert.ToInt32(Console.ReadLine());

while(num != a) {
    if(num < a){
        Console.WriteLine("不对不对, 太小了");
    }
    else {
        Console.WriteLine("不对不对, 太大了");
    }
    Console.WriteLine("再猜一次吧:");
    num = Convert.ToInt32(Console.ReadLine());
}
Console.WriteLine("恭喜你猜对了!");
```

### 例题 2-1 [竞选社长](https://www.nowcoder.com/practice/45a30e3ef51040ed8a7674984d6d1553?tpId=107&&tqId=33321&rp=1&ru=/ta/beginner-programmers&qru=/ta/beginner-programmers/question-ranking)

假设电子电路社要竞选下一届社长，有两名候选人分别是A和B，社团每名同学必须并且只能投一票，最终得票多的人为社长.

输入包含若干行的字符，每行仅包含A或B，输入以字符0结束。（原题为一行字符序列）

```csharp
string str = Console.ReadLine();
int a=0, b=0;
while(str != "0") {
    if(str == "A"){
        a++;
    }
    else {
        b++;
    }
    str = Console.ReadLine(); // 不要忘记重新读取下一行
}

if(a > b){
    Console.WriteLine("A");
}
else if(a < b){
    Console.WriteLine("B");
}
else {
    Console.WriteLine("E");
}
```

## `for` 循环

以下代码列是一个简单的 `for` 语句，它循环遍历其代码块（即被大括号括起来的内容）十次，并打印 `i` 的当前值。

```csharp
for (int i=0; i < 10; i++) {
  Console.WriteLine("i的值为: {0}", i);
}
```

大括号包起来的代码块部分很好理解，让我们来看看小括号里的内容：

小括号里被分号 `;` 分为三个部分，分别表示：

1. 在进入循环语句和判断条件之前执行的语句，无论循环是否执行这个语句都只会被执行一次
2. 循环判断的条件，与 `while` 语句同理
3. 每次执行完大括号里的内容之后执行的语句，注意是在执行完该语句之后才会再次判断条件

刚刚的学习 `while` 循环时展示的代码可以用 `for` 循环更简单的写出来：

```csharp
for (int a=5; a < 10; a++) {
    Console.WriteLine("a 的值： {0}", a);
}
```

再对比刚刚的代码看：

```csharp
int a = 5; // 被小括号里的第一部分代替
while (a < 10) { // 被小括号里的第二部分代替
    Console.WriteLine("a 的值： {0}", a);
    a++; // 被小括号里的第三部分代替
}
```

注意小括号里第一部分写为 `int a` 和在循环外写 `int a` 的区别：

```csharp
for (int a=5; a < 10; a++) {
    Console.WriteLine("a 的值： {0}", a);
}
Console.WriteLine(a); // 会报错告诉你 a 没有定义
```

换句话说在括号里定义的 `a` 就只会在循环的范围内生效

如果想使用 a 的值请像下面这么写：

```csharp
int a;
for (a=5; a < 10; a++) {
    Console.WriteLine("a 的值： {0}", a);
}
Console.WriteLine(a); // 正常执行，输出10
```

也请注意最后 `a` 的值为 10 而不是 9。考虑反证法，如果 a 为 9 则还满足循环的条件，则会继续执行循环的内容，所以 a 一定不是 9

### 例题 2-2 FizzBuzz 问题

每行输出一个数字 从 1 到 100，满足以下规则：

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
// 注意这里用的是 <= , 如果想模仿上面的例子使用 <, 请写 101
for(int i=1; i <= 100; i++) {
    if(i % 3 == 0 && i % 5 == 0) { // 如果同时能被 3 和 5 整除执行
        Console.WriteLine("{0} - FizzBuzz", i);
    }
    // 注意 else, 不能被同时整除的时候却能被 3 整除才执行
    else if(i % 3 == 0) { 
        Console.WriteLine("{0} - Fizz", i);
    }
    // 同样注意 else, 不能被同时整除 也不能被 3 整除 却能被 5 整除执行
    else if(i % 5 == 0) {
        Console.WriteLine("{0} - Buzz", i);
    }
    else { // 上述情况都不满足说明不能被任何一个整除
        Console.WriteLine(i);
    }
}
```

无代码注释版：

```csharp
for(int i=1; i <= 100; i++) {
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

请注意括号里三个部分不同就会导致循环不同的结果：(注释为循环时 `i` 的范围)

```csharp
for (int i=1; i <= 10; i++) {  } // [1,10]
for (int i=1; i < 10; i++) {  } // [1,9]
for (int i=0; i <= 10; i++) {  } // [0, 10]
for (int i=10; i >= 1; i--) {  } // [1,10] 逆序
for (int i=10; i > 1; i--) {  } // [2,10] 逆序
for (int i=1; i <= 10; i += 2) {  } // {1, 3, 5, 7, 9}
```

## 嵌套循环

循环是可以嵌套的，当出现嵌套循环的时候，先执行内层循环，内层循环执行完一遍之后再回到外层的循环，再从外层循环进入内层循环，类似数学中的 $\sum\sum$，又类似平常说的“先从上到下 再从左到右” 这种也可以理解为嵌套循环。让我们看一个例子：

```csharp
for(int i=5; i < 10; i++) {
    Console.WriteLine("i 的值： {0}", i);
    for(int j=5; j < 8; j++) {
        Console.WriteLine("    j 的值： {0}", j);
    }
}
```

{% note danger %}

请注意在嵌套循环的时候两个变量 `i` 和 `j` 不要错写成一样的，会引起混淆，就像一个班里有两个人都叫小明的时候你直接喊“小明”会不知道你指的是谁。

{% endnote %}

{% hideToggle 输出 %}

```
i 的值： 5
    j 的值： 5
    j 的值： 6
    j 的值： 7
i 的值： 6
    j 的值： 5
    j 的值： 6
    j 的值： 7
i 的值： 7
    j 的值： 5
    j 的值： 6
    j 的值： 7
i 的值： 8
    j 的值： 5
    j 的值： 6
    j 的值： 7
i 的值： 9
    j 的值： 5
    j 的值： 6
    j 的值： 7
```

{% endhideToggle %}

### 例题 2-3 [等腰直角三角形](https://www.nowcoder.com/practice/2cdea429fa414fbba26e6c821724ca06?tpId=107&&tqId=33340&rp=1&ru=/ta/beginner-programmers&qru=/ta/beginner-programmers/question-ranking)

KiKi学习了循环，BoBo老师给他出了一系列打印图案的练习，该任务是打印用“*”组成的翻转直角三角形图案。(原题为多组数据，这里简化为一组)

输入一个数字即等腰直角三角形的侧边长，当输入为 5 时输出如下：

```
* * * * *
* * * * 
* * *
* *
*
```

示例代码：

```csharp
int n = Convert.ToInt32(Console.ReadLine());
for(int i=1; i <= n; i++) {
    for(int j=i; j <= n; j++) { // 注意这里 j 的初始值设为 i, 这样才能每次输出星号个数递减
        Console.Write("* ");
    }
    Console.WriteLine(); // 输出空行
}
```

## 循环控制语句

{% note info %}

以下内容对 `for` 和 `while` 均适用

{% endnote %}

### `break` 语句

`break` 表示终止循环，当在循环里遇到 `break` 语句时，循环会立即终止，且程序流将继续执行紧接着循环语句之后的语句。例如：

```csharp
for(int i=5; i < 10; i++) {
    if(i == 8) break;
    Console.WriteLine("i 的值： {0}", i);
}
Console.WriteLine("end loop");
```

{% hideToggle 输出 %}

```
i 的值： 5
i 的值： 6
i 的值： 7
end loop
```

{% endhideToggle %}

当 `break` 语句用在嵌套循环中，只会跳出最内层的循环，例如：

```csharp
for (int i = 5; i < 10; i++) {
    Console.WriteLine("i 的值： {0}", i);
    for (int j=5; j < 9; j++) {
        if(j == 7) break;
        Console.WriteLine("    j 的值： {0}", j);
    }
}
```

{% hideToggle 输出 %}

```
i 的值： 5
    j 的值： 5
    j 的值： 6
i 的值： 6
    j 的值： 5
    j 的值： 6
i 的值： 7
    j 的值： 5
    j 的值： 6
i 的值： 8
    j 的值： 5
    j 的值： 6
i 的值： 9
    j 的值： 5
    j 的值： 6
```

{% endhideToggle %}

### `continue` 语句

`continue` 语句与 `break` 语句类似，但 `continue` 语句的意思是 停止当前循环体里语句的执行，跳到循环的开始，（对于 `for` 循环）执行括号里第三部分的语句，然后重新判断循环条件决定是否继续循环。

例如把上面的例子中的 `break` 改成 `continue`：

```csharp
for(int i=5; i < 10; i++) {
    if(i == 8) continue;
    Console.WriteLine("i 的值： {0}", i);
}
Console.WriteLine("end loop");
```

{% hideToggle 输出 %}

```
i 的值： 5
i 的值： 6
i 的值： 7
i 的值： 9
end loop
```

{% endhideToggle %}

注意这里跳过了 `i = 8` 时的情况直接输出了 `i = 9` 的情况

# 练习

## 2-1 阶乘  (P5739)
输入 `n`, 输出 `n` 的阶乘(n <= 12)

## 2-2 aabb
输出所有形如 aabb 的完全平方数

## 2-3 最高分与最低分之差

第一行输入一个数 n, 然后n行每行一个整数代表一个人的成绩, 求出最高分和最低分的差值

{% tabs 2-3 %}
<!-- tab 输入 -->

5
98 
100 
99 
97 
95 

<!-- endtab -->

<!-- tab 输出 -->

5

<!-- endtab -->
{% endtabs %}

## 2-4 [RPG游戏](https://docs.microsoft.com/zh-cn/learn/modules/csharp-do-while/3-challenge)

在大部分角色扮演游戏中，玩家角色会与NPC战斗。在此练习中，我们归纳出战斗过程的本质。 英雄和怪物在开始时的生命值相同。 在英雄攻击时，它们将生成一个随机值，该值将从怪物的生命值中减去。 如果怪物的生命值大于零，则会轮到它们攻击英雄。 只要英雄和怪物的生命值都大于零，战斗就会继续进行。

为游戏实现以下规则：

**游戏规则**

- 英雄和怪物在开始时的生命值为 10。
- 所有攻击都是介于 1 到 10 之间的随机值。
- 英雄首先攻击。
- 输出怪物损失的生命值，以及剩余的生命值。
- 如果怪物的生命值大于 0，则它会攻击英雄。
- 输出英雄损失的生命值，以及剩余的生命值。
- 继续此攻击顺序，直到怪物或英雄任意一方的生命值为零或更低。
- 输出胜利者。