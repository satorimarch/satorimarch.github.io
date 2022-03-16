---
title: 'C#教程[5] 方法'
tag:
  - c#
categories:
  - 电子电路社
  - c#教程
mathjax: true
sticky: 1
abbrlink: 1926cc4
date: 2022-02-03 00:00:00
---

# 方法的定义

{% note info flat %}
在本节之前为了便于理解故将方法称为函数, 本节之后为了与专有名词接轨所以使用方法一词
{% endnote %}

我们已经用过很多内置的方法了, 例如 `WriteLine()`, `ToInt32()`, `Max()` 等等, 其实我们也可以定义方法, 定义方法的语法如下:

```csharp
[访问修饰符] static 返回值类型 方法名([参数列表]）
{
    //方法体
}
```

让我们以下面这个方法为例, 分析一下定义方法的语法的含义

```csharp
public int square(int a)
{
    return a * a;
}
```

这个方法接收一个 `int` 类型的参数并记为 `a`, 然后返回 `a` 的平方

 - `public` 是访问修饰符, 除此之外还有 `private`, `protected` 等, 本文中所有的访问修饰符更改都不会影响结果, 先不用在意

 - 其中第一个 `int` 表示的是方法的返回值的类型, 括号里的第一个(也是唯一一个) `int` 表示接收的第一个参数是 `int` 类型的, 将这个参数记为 `a`, 可以在方法体里用 `a` 来使用

 - 方法体就是调用这个方法之后执行的代码

 - `return` 关键字表示将后面的值作为方法的返回值, **然后立刻结束该方法**

我们需要把这个方法的定义写在 `Main` 方法外面, 让我们试着像调用 `Max()` 方法那样调用它:

```csharp
class Program
{
    public int square(int a)
    {
        return a * a;
    }

    static void Main(string[] args)
    {
        Console.WriteLine(square(5));
    }
}
```

然后会发现报错了:

{% note danger flat %}
对象引用对于非静态的字段、方法或属性“Program.square(int)”是必需的
{% endnote %}

这句话大家可能看着云里雾里的, 但是也许大概能猜出两点:
1. 对于**非静态**的xxx是必须的, 那如果是静态的就非必须了?
2. 似乎缺少一个对象?

对于第一种想法只要在方法的定义里加上 `static` 修饰符就可以了(`static` 这个词就是"静态"的意思):

```csharp
class Program
{
    public static int square(int a)
    {
        return a * a;
    }

    static void Main(string[] args)
    {
        Console.WriteLine(square(5));
    }
}
```

现在就可以正常运行了, 加上 `static` 修饰符的方法叫做静态方法

我们在第三节"再谈类型"详细讲过什么是"静态", 当时是这么说的:

> 静态是一种总体的概念，与整个类有关，和每个单独的对象没有关系。

大家还记得 `Program` 也是一个类吗, 这里的类指的就是 `Program` 类, 这个方法的返回值只与它接受的参数有关系, 与其他的东西没有关系, 所以可以设定为静态的。

第二种做法需要自己定义一个类

还记得当时我们是怎么使用 `Random` 类中的 `Next()` 方法的吗? `Random` 是一个类, 我们先 `new` 了一个 `Random` 类的对象称作 `rd`, 然后再用 `.` 调用 `rd` 对象的方法 `Next()`
```csharp
Random rd = new Random();
int a = rd.Next();
```

仿照我们代码中的 `Program` 类, 再定义一个类: (具体有关类的概念会在下一节讲解)

```csharp
class Calculator
{
    public int square(int a)
    {
        return a * a;
    }
}
```

然后把这个类和 `Program` 类并列放在一起, 再用类似的做法调用 `square` 方法:

```csharp
using System;

namespace csharp
{
    class Program
    {
        static void Main(string[] args)
        {
            Calculator cal = new Calculator();
            Console.WriteLine(cal.square(5));
        }
    }

    class Calculator // 类的定义从这开始
    {
        public int square(int a) // 必须使用public
        {
            return a * a;
        }
    }
}
```

这种没有 `static` 修饰符的方法叫做非静态方法或者实例方法

因为 `square` 的结果只与参数 `a` 有关所以其实在 `Calculator` 类中也可以使用静态方法:

```csharp
using System;

namespace csharp
{
    class Program
    {
        static void Main(string[] args)
        {
            // 不需要new一个Calculator
            int a = Calculator.square(5); 
            Console.WriteLine(a);
        }
    }

    class Calculator
    {
        public static int square(int a) // 必须使用public
        {
            return a * a;
        }
    }
}
```


后文均使用静态方法, 但所述内容对实例方法也适用, 而实例方法会在下一节介绍面向对象相关内容用到

## void 关键字

方法并不一定要有返回值, 如果想要定义一个没有返回值的方法可以使用 `void` 关键字代替原来的返回值类型的位置:
```csharp
public static void output(string name)
{
    Console.WriteLine("My name is" + name);
}
```

然后正常调用:
```csharp
public static void output(string name)
{
    Console.WriteLine("My name is " + name);
}

static void Main(string[] args)
{
    output("jiangdu");
}
```

无返回值方法也可以用 `return;` 来让方法立刻结束:
```csharp
public static void output(string name)
{
    if(name == "jiangdu") {
        return;
    }
    Console.WriteLine("My name is " + name);
}

static void Main(string[] args)
{
    output("jiangdu");
}
```

上面的代码没有输出

# 方法的参数

方法的参数可以是任意类型, 也可以有多个参数

```csharp
public static double Max(double a, double b)
{
    if(a >= b) return a;
    else return b; 
}
```

注意多个参数的时候参数的类型可以不同, 但是一定要注意输入的顺序:

```csharp
// Info 常用来表示 Infomation 的缩写
public static void PrintInfo(string name, int index) 
{
    if(index <= 0) {
        Console.WriteLine("序号无效");
    }
    else{
        Console.WriteLine("第{0}个学生: {1}", index, name);
    }
}
```

调用的时候需要按照参数列表的顺序来:

```csharp
static void Main(string[] args)
{
    PrintInfo("jiangdu", 1); // 正确
    PrintInfo(1, "jiangdu"); // 报错
}
```

## 例题5-1 遍历查找

给定一个一维数组, 返回数组中的最大值

```csharp
static int GetMax(int[] array)
{
    int max = array[0];
    for (int i = 1; i < array.Length; i++){
        if (array[i] > max)
            max = array[i];
    }
    return max;
}
```

使用随机数来测试你的代码:
```csharp
static void Main(string[] args)
{
    int n = 10;
    int[] a = new int[n]; // 开一个大小为 10 的一维数组, 下标范围[0,9]
    Random rd = new Random(); // Random对象不需要每次重新生成, 所以放在循环外面

    for(int i=0; i < n; i++){
        a[i] = rd.Next(0, 101); // 左闭右开
        Console.Write(a[i] + " ");
    }

    Console.Write("\n"); // 双引号中的 \n 表示换行符
    // Console.WriteLine(); // 这样也可以直接输出换行
    Console.WriteLine(GetMax(a));
}
```

## 引用传递参数

在解释这段的标题前先思考一下, 如何交换两个整数呢? 是`x = y; y = x;` 吗, 显然不是, 因为在 `x = y;` 之后, `x` 保存的就是 `y` 的值了, 所以 `y = x;` 之后两个变量保存的都是原来 `y` 的值

所以应该用一个变量临时存储一下原来 `x` 的值:

```csharp
int temp = x; // 把 x 的值保存到 temp
x = y; // 把 y 的值保存到 x
y = temp; // 把 temp 的值(即交换前 x 的值)保存到 y
```

{% note info flat %}
temp 是 temporary 的缩写, 意思是"临时的"
{% endnote %}

让我们试着写一个交换两个整数的方法(有BUG):
```csharp
public static void swap(int x, int y)
{
    int temp = x;
    x = y;
    y = temp;
}
```

在主函数中调用这个方法, 然后运行一下
```csharp
static void Main(string[] args)
{
    int a = 5, b = 10;
    swap(a, b);
    Console.WriteLine("{0} {1}", a, b);
}
```

你会发现两个数并没有完成交换, 这就是因为我们传入参数的时候是按值传递的参数

在你传递参数的时候, 传递的只是 `a` 变量的值 `5` 和 `b` 变量的值 `10`, 在调用的时候把这两个值复制了一遍, 和原来的变量没有关系, 我们只交换了那两个复制之后的值, 而没有交换原来的值(复制出来的值会在方法运行结束后销毁)

这样的设计是为了保护原本的参数不变

方法的参数列表中的 `x` 和 `y` 称为形式参数, 简称形参, 是出现在方法的定义中用来代表传入的值的; 而具体调用时的参数 `a` 和 `b` 称为实际参数, 简称实参, 出现在调用方法的时候

为了实现 `swap` 方法, 就要用到引用

 > 引用参数是一个对变量的内存位置的引用。当按引用传递参数时，与值参数不同的是，它不会为这些参数创建一个新的存储位置。引用参数表示与提供给方法的实际参数具有相同的内存位置。

如果把变量比作房子, 引用就像是房子的地址, 如果传入的参数是变量的地址的话, 那在方法里也可以按照这个地址找到原来的变量. 所以按引用传参的话, 在方法里也能更改原本的变量

使用 `ref` 关键字来声明引用参数:

```csharp
public void swap(ref int x, ref int y)
{
    int temp = x;
    x = y;
    y = temp;
}
```

现在再测试, 就可以正常执行了

# 递归

从刚刚在方法里调用 `WriteLine()` 方法以及 `Main` 方法能够调用其他方法就能看出, 方法之间是可以互相调用的. 那么, 一个方法能不能调用自身呢? 答案是肯定的, 不过先不要急着写出像下面这样的代码:

```csharp
public static void function()
{
    function();
}
```

如果你试着调用它然后运行, 过几秒或更久之后就会有这样的报错:
{% note danger flat %}
发生异常: CLR/System.StackOverflowException
{% endnote %}

由于 `function` 方法一直在调用自身, 而内层的方法返回之前外层的 `function` 方法不会结束, 而内层的方法又会再次调用 `function`, 然后无限重复.

这就有点像大家从小就听过的故事：从前有座山，山里有座庙，庙里有一个老和尚和一个小和尚讲故事。从前有座山，山里有座庙，庙里有一个老和尚和一个小和尚讲故事...

关注刚刚报错信息中的 `StackOverflow` 这个词, `Stack` 是栈的意思, 这里指的是调用栈, 你可以理解为是一种容器, 每当方法调用的时候就会往里装东西, 例如按值传递的时候会把复制之后的值放在这里; 当方法返回的时候就会把对应的东西扔掉

`StackOverflow` 就是栈溢出,  因为那个方法一直在无限重复调用自身, 而每次调用都会往栈里装东西, 所以最后装满了放不下了, 然后你的程序就崩溃了.

因此我们需要给调用自身一个终止条件:
```csharp
// 递归的英文是 Recursion
public static void Recursion(int n)
{
    if(n == 0){
        return;
    }
    Recursion(n-1);
    Console.WriteLine(n);
}
static void Main()
{
    Recursion(5);
}
```

输出是:
{% note default %}
0
1
2
3
4
5
{% endnote %}

调用过程类似 Recursion(5) -> Recursion(5) -> ... -> Recursion(0) 由于到了 `n == 0` 的时候不再调用自身, 所以 最内层的 `Recursion(0)` 输出之后可以返回, 之后次内层的 `Recursion(1)` 就可以输出并返回了...最终 `Recursion(5)` 可以正常结束

这样方法自己调用自己的技巧就叫做递归

关于递归有很多笑话: 要理解递归，就得先了解什么是递归。

实际上这句话就是一个递归。
了解递归(1) -> 了解递归(2) -> ...
当你从这句话中悟出什么是递归的时候, 就可以一层层返回了

注意刚刚代码中的 `Recursion(n-1);` 和 `Console.WriteLine(n);` 的顺序, 如果颠倒一下输出就会完全相反

```csharp
public static void Recursion(int n)
{
    if(n == 0){
        return;
    }
    Console.WriteLine(n);
    Recursion(n-1);
}
```

因为每个方法会先输出自己的 `n` 的值再调用自身, 所以输出会先从 `5` 开始, `0` 结束

## 例题5-2 斐波那契数列

斐波那契数列的定义:

$$
\left\{ \begin{array} { l } { f ( n ) = f ( n - 1 ) + f ( n - 2 ), n \ge 3 } \\ { f ( 1 ) = f(2) = 1 } \end{array} \right.
$$

也就是: 1, 1, 2, 3, 5, 8, 13, 21, 34, 55...

输出斐波那契数列的第 `x` 个数

递归代码:

```csharp
public static int Fib(int n)
{
    if(n == 1 || n == 2){
        return 1;
    }
    return Fib(n-1) + Fib(n-2);
}
```

由此可见, 数学上的递推公式可以直观的用递归写出来, 很多算法也都是用递归来实现的, 例如dfs

由于递归时调用的过程是这样的:

![](https://s6.jpg.cm/2022/02/07/LoqS32.png)

注意到这张图里 `fib(3)` 以及它下面会调用的方法这个整体会被计算两遍, 因此刚刚的递归会产生大量重复运算, 而使用下文展示的循环则只会计算一次, 所以这里用循环会比递归要快:

```csharp
int n = 10;
int[] fib = new int[n+1];

fib[1] = fib[2] = 1;
for(int i = 3; i <= n; i++){
    fib[i] = fib[i-1] + fib[i-2];
}
Console.WriteLine(fib[n]);
```

甚至还可以用技巧来省去数组, 节约内存:

```csharp
int n = 10;

int first = 1, second = 1, third = 2;
for(int i = 3; i <= n; i++){
    third = first + second;
    first = second;
    second = third;
}
Console.WriteLine(third);
```

不过很多更复杂的情况下递归容易写出, 而循环可能非常难写

在 `n` 的取值大到能体会到速度差别之前就会因为 `fib[n]` 太大超过 `int` 的表示范围而输出错误的结果, 如果想测试两段代码的速度的话, 请在过程中对答案取模, 例如:
```csharp
DateTime startTime = DateTime.Now; // 保存当前时间

int n = 10;
int mod = 1000000000;

int first = 1, second = 1, third = 2;
for(int i = 3; i <= n; i++){
    third = (first + second) % mod;
    first = second;
    second = third;
}
Console.WriteLine(third);

DateTime finishTime = DateTime.Now; // 保存当前时间
double deltaTime = (finishTime - startTime).TotalMilliseconds; // 计算时间差

Console.WriteLine("use {0} ms", deltaTime);
```

递归也可以改写为只计算一次的：

```csharp
public static int Fib(int n, int[] fib)
{
    if(n == 1 || n == 2){
        return 1;
    }
    if(fib[n] != 0) return fib[n];
    fib[n] = Fib(n-1, fib) + Fib(n-2, fib);
    return fib[n];
}

static void Main(string[] args)
{
    int n = 40;
    int[] fib = new int[n+1];

    Console.WriteLine(Fib(n, fib));
}
```

这样借助 `fib` 数组将递归已经计算过的结果存储下来, 避免重复运算, 称为记忆化搜索
