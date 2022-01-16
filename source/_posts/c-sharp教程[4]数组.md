---
title: 'C#教程[4] 数组'
tag:
  - c#
categories:
  - 电子电路社
  - c#教程
mathjax: true
abbrlink: b5342c8
date: 2022-1-16 00:00:00
---

# 声明数组

数组是一个存储相同类型数据的固定大小的顺序集合。用简单的话来说就是，数组可以用单个变量名来访问很多同一类型的数据，而不需要声明很多的变量。

假设我们正在做一个把所有一共 `n` 个学生的分数进行排名的程序，那么我们就要储存所有学生的分数，由于 `n` 可能很大而且不是一个固定的值，所以我们无法为每个学生都声明一个变量来存储，就算那么做也无法进行排名。这时候我们需要使用数组。

声明数组的语法如下：

```csharp
type[] arrayName; // array 就是数组的英文
```

例如：

```csharp
int[] score;
```

但如果这样使用数组的话会报错：

{% note danger flat %}
error CS0165: 使用了未赋值的局部变量“score”
{% endnote %}

这是因为数组声明之后并不会初始化，所以还需要在声明的时候使用 `new` 关键字来创建数组的实例（关于什么是 `new` 操作符请见上一篇教程 不过暂时不懂问题也不大），例如：

```csharp
int[] score = new int[5];
```

其中方括号里的数组表示的是数组的大小，数组的长度是固定的，所以必须说明它的大小。

{% note info flat %}
你可以声明任意类型的数组, 比如 `double`, `string` 等, 还有更复杂的还没学到的, 现在只用 `int` 举例
{% endnote %}

在定义数组之后，我们可以用 `arrayName[index]` 来访问叫做 `arrayName` 的数组中的第 `index+1` 个元素，其中方括号中的内容叫做数组的下标或者索引(index就是索引的英文)。

{% note danger flat %}
请注意，数组是从 0 开始计数的，所以数组中的第一个元素应为 `arrayName[0]` 而非 `arrayName[1]`
{% endnote %}

你可以在声明的时候对数组中的元素赋初始值，例如：
```csharp
int[] scores = new int[5]{98, 97, 94, 92, 95};
```

此时 `scores` 数组中第一个元素是 98, 索引是 0, 最后一个元素是95, 索引是 4 

使用 `score[index]` 访问数组中的元素:
```csharp
int[] scores = new int[5]{98, 97, 94, 92, 95};
Console.WriteLine(scores[1]);
```

输出为 `97`

也可以这样更改数组中的元素:
```csharp
int[] scores = new int[5]{98, 97, 94, 92, 95};
scores[1] = 99;
```

{% note danger flat %}
请时刻留意数组的范围, 因为数组从 0 开始
{% endnote %}

如果你试图访问不存在的下标, 例如:
```csharp
int[] scores = new int[5];
scores[5] = 1;
```

会收到这样的报错信息:

{% note danger flat %}
Index was outside the bounds of the array.
{% endnote %}

翻译过来就是: 下标超过了数组的边界, 也就是"数组越界"

# 遍历数组

为了一次性访问数组中的诸多元素, 可以使用第二节学过的循环：

```csharp
int[] scores = new int[5];
for(int i=0; i < 5; i++){ // 注意这里的条件
Console.WriteLine(scores[i]);
```

输出估计大家都能猜到：
{% hideToggle 查看输出 %}
98
97
94
92
95
{% endhideToggle %}

也可以试试用循环进行初始化
```csharp
int[] scores = new int[5];
for(int i=0; i < 5; i++){ // 注意这里的条件
    scores[i] = i;
```

当你不知道数组有多大的时候，可以使用 `arrayName.Length` 访问数组的长度，上面的代码可以写为：
```csharp
int[] scores = new int[5]{98, 97, 94, 92, 95};
for(int i=0; i < scores.Length; i++){ // 注意这里的条件
scores[i] = i;
```

注意 `Length` 后面不要写括号，因为这不是个函数

为了方便起见, 你也可以不用索引为 0 的元素, 比如要存 5 个元素的时候写为这样:
```csharp
int[] scores = new int[6];
for(int i=1; i <= 5; i++){
    scores[i] = i;
```

{% note danger flat %}
如果这么用的话请一定要注意给数组多分配一个长度, 因为第 0 个被空出来了
以及注意 `for` 循环时一定要循环到 `<= arrayName.Length` 这样才能遍历全部元素
{% endnote %}


## `foreach` 语句
不过其实我们有更简单的循环方法，之前在讲循环的时候因为没讲过数组所以没讲，就是使用 `foreach` 语句

类似 `python` 中的 `for item in array:`，你可以直接用 `foreach` 来访问数组中的每一个值，例如：
```csharp
int[] scores = new int[5]{98, 97, 94, 92, 95};
foreach (int i in scores){
Console.WriteLine(i);              
}
```

注意 `i` 本身就是数组中的一个元素，而不是索引，所以应该直接输出 `i`

请注意 `foreach` 语句中的 `i` 是不能被赋值的, 也就是说只能用 `foreach` 来查询数组中的值而不能用来赋值

## 例题 4-1 最高分
求所有学生中的最高分数

```csharp
int[] scores = new int[5]{98, 97, 94, 92, 95};
int maxScore = 0;
foreach (int item in scores){
    maxScore = Math.Max(item, maxScore);
}
Console.WriteLine(maxScore);
```

其中 `Math.Max()` 是一个我们之前没有用过的函数, 不过顾名思义, 就是返回两个数中的最大值（`double` 等数据类型也是可以的）

如果你不愿意使用这个函数, 可以改为：

```csharp
int[] scores = new int[5]{98, 97, 94, 92, 95};
int maxScore = 0;
foreach (int item in scores){
    if(maxScore < item) maxScore = item;
}
Console.WriteLine(maxScore);
```

也就是说只在 `maxScore` 比 `item` 小的时候才用 `item` 更新 `maxScore`, 这样 `maxScore` 就是 `scores` 数组中的最大值了

那么回到本文最开始的问题, 怎么给 `n` 个学生的分数进行排名呢, 不用想怎么实现排序, 因为 `c#` 有给数组排序的函数: `Array.Sort(arrayName)`
这里的 `Array` 是一个类, 包含很多与数组有关的函数

```csharp
int[] scores = new int[5]{98, 97, 94, 92, 95};
Array.Sort(scores);
```

这样就给 `scores` 数组排好序了, `sort` 排序默认是从小到大, 所以我们可以反着遍历数组来输出从大到小的值

完成了最初的目标, 再改为需要读入数据的版本：

```csharp
int n = Convert.ToInt32(Console.ReadLine()); // 学生总数

int[] scores = new int[n];
for(int i=0; i < n; i++){
    scores[i] = Convert.ToInt32(Console.ReadLine()); // 每个学生的分数
}

Array.Sort(scores);

for(int i=n-1; i >= 0; i--){
    Console.WriteLine(scores[i]);
}
```

如果你嫌倒着遍历麻烦可以使用 `Array.Reverse()` 来翻转数组, 这样就能正着遍历了:
```csharp
// 前面的代码相同, 略去
Array.Sort(scores);
Array.Reverse(scores);

for(int i=0; i < n; i++){
    Console.WriteLine(scores[i]);
}
```

{% note warning flat %}
注意, 如果你要把第一个空过去的话不能直接 `Array.Sort(arrayName)`, 因为这样会把第 0 个元素 `0` 也算进去排序
{% endnote %}

`Sort` 有很多重载, 其中一个是 `Sort(arrayName, index, length)` , `index` 是排序范围的起始索引, `length` 是排序的元素个数
`Reverse` 也有类似的用法

所以要空过去第 0 个的话, 应该改为:
```csharp
int n = Convert.ToInt32(Console.ReadLine()); // 学生总数

int[] scores = new int[n+1]; // 因为后面空过去了第 0 个元素所以这里要声明为 n+1, 否则会数组越界
for(int i=1; i <= n; i++){
    scores[i] = Convert.ToInt32(Console.ReadLine());
}

Array.Sort(scores, 1, n);
Array.Reverse(scores, 1, n);

for(int i=1; i <= n; i++){
    Console.WriteLine(scores[i]);
}
```

再加点细节:

```csharp
int n;
Console.Write("请输入学生总数: ");
n = Convert.ToInt32(Console.ReadLine());

int[] scores = new int[n]; 
for(int i=1; i <= n; i++){
    Console.Write("请输入第{0}个学生的分数: ", i);
    scores[i] = Convert.ToInt32(Console.ReadLine());
}

Array.Sort(scores, 1, n);
Array.Reverse(scores, 1, n);

for(int i=1; i <= n; i++){
    Console.WriteLine("第{0}名的分数: {1}", i, scores[i]);
}
```

## 扩展阅读
{% note info flat %}
本段可以跳过
{% endnote %}

你会发现，这样我们只对分数进行了排序，而没法将分数与人名对应, 做法有很多种, 这里只介绍其中一种

可以想到, 我们需要的是一个能够同时保存 `int` 类型的分数和 `string` 类型的字符串的数组(之前说过数组可以声明更复杂类型的数组), 再用 `Sort` 对它进行排序, 而我们还没学过自定义类型, 怎么办呢

好在 `c#` 提供了 `Tuple` 类型(中文为元组), 可以由多个元素组成(最多8个), 用 `tupleName.Item1` 访问第一个元素(以此类推)

用 `Tuple<int, string>` 来表示第一个元素为 `int` 类型, 第二个元素为 `string` 类型的 `Tuple`

所以我们创建一个 `Tuple<int, string>` 类型的数组
`Tuple` 类型已经写好了 `<` 操作符, 先比较第一个元素的大小, 如果相等再比较第二个(以此类推), 所以可以直接使用 `sort`

据此可以将上面的代码改为:
```csharp
int n;
Console.Write("请输入学生总数: ");
n = Convert.ToInt32(Console.ReadLine());

Tuple<int, string>[] scores = new Tuple<int, string>[n+1];
for(int i=1; i <= n; i++){
    Console.Write("请输入第{0}个学生的姓名: ", i);
    string b = Console.ReadLine();
    Console.Write("请输入第{0}个学生的分数: ", i);
    int a = Convert.ToInt32(Console.ReadLine());

    scores[i] = Tuple.Create(a, b);
}

Array.Sort(scores, 1, n);
Array.Reverse(scores, 1, n);

for(int i=1; i <= n; i++){
    Console.WriteLine("第{0, -2}名:  {1, -5}{2, -5}", i, scores[i].Item1, scores[i].Item2);
}
```

最后输出时的占位符 `{0, -2}` 中, 第一个村阿叔 `0` 的意思与之前的 `{0}` 一样, 表示后面下标为 `0` 的对象, `-2` (的绝对值)表示输出的长度, 不足的补成空格, 负号表示左对齐, 这样是为了输出的时候同一列数据可以左对齐, 好看一点, 你也可以不用

# 数组相关函数
这里介绍一些相对常用的函数

## `Array.Clear()`
用来清空数组
```csharp
Array.Clear(arrayName);
Array.Clear(arrayName, index, length);
```

## `strName.Split()`
注意这个不是对数组进行操作
这个函数的用处是, 将一个字符串按照你输入的分隔符分成由若干个字符串组成的 `string` 数组, 然后返回这个 `string` 数组

```csharp
stringName.Split(Seperator);
```

使用例:
```csharp
string a = "a ab abc abcd";
string[] strArray = a.Split(" ");
foreach(string i in strArray){
    Console.WriteLine(i);
}
```

这里会按空格来把 `a` 字符串分成四个字符串, 存到 `strArray` 这个字符串数组中

用这种方法我们就可以在一行内读入多个数据了

## 例题 4-2 逆序输出
一行输入若干个整数, 在一行内倒序输出它们
```csharp
string temp = Console.ReadLine();
string[] a = temp.Split(" ");
for(int i=a.Length-1; i >= 0; i--){
    Console.Write("{0} ", a[i]);
}
```

# 二维数组
之前说过数组可以声明更复杂类型的数组, 那么大家想没想过, 数组中的元素也可以是另一个数组呢!

数组中的子数组长度是可以不相同的, 那种叫做交错数组, 不太常用, 不在本文讨论范围之内
`c#` 中的二维数组仅指每个子数组的长度都相同的那种

一个包含 x 个子数组, 其中每个子数组有 y 个元素的二维数组可以被看做一个 x 行 y 列的表格

声明二维数组的语法如下:
```csharp
type[,] array = new type[x, y];
```

例如声明一个 3 行 4 列的数组并初始化:
```csharp
int [,] a = new int [3,4] {
    {0, 1, 2,  3},
    {4, 5, 6,  7},
    {8, 9, 10, 11}
};
```

换行当然是可以删掉的, 写成:
```csharp
int [,] a = new int [3,4] { {0, 1, 2, 3}, {4, 5, 6, 7}, {8, 9, 10, 11} };
```

我们可以用 `a[i][j]` 来访问这个二维数组中第 `i` 行 第 `j` 列的元素, 例如:

```csharp
int [,] a = new int [3,4] { {0, 1, 2, 3}, {4, 5, 6, 7}, {8, 9, 10, 11} };
Console.WriteLine(a[1][2]);
```

从本质上讲, `a[1]` 访问的是 `a` 中的第 1 个元素(从 0 开始), 也就是一个数组 `{4, 5, 6, 7}`
而例如 `a[1, 2]` 也就是访问 `a[2]` 中的第 2 个元素, 也就是 数组 `{4, 5, 6, 7}` 中的第 2 个元素, 所以 `a[i][j]` 为 6

不过在平时使用时不需过多关注它本质的意思, 当成表格就好

循环访问二维数组的元素如下:
```csharp
int [,] a = new int [3,4] { {0, 1, 2, 3}, {4, 5, 6, 7}, {8, 9, 10, 11} };
for(int i=0; i < 3; i++){
    for(int j=0; j < 4; j++){
        Console.WriteLine("({0}, {1}): {2}", i, j, a[i, j]);
    }
}
```

其实 `foreach` 也可以遍历二维数组中的所有元素, 但是一般情况下我们可能会需要数据的坐标(指位于的行和列), 那种情况下就不能用了

```csharp
int [,] a = new int [3,4] { {0, 1, 2, 3}, {4, 5, 6, 7}, {8, 9, 10, 11} };
foreach(int item in a){
    Console.WriteLine(item);
}
```

# 综合运用: 扫雷的棋盘生成

大家都玩过扫雷吧, 我们这里做一个 `mapRow` × `mapColumn` 大小的棋盘(二维数组), 上面有 `mineNum` 个雷
我们用 `map[i]` 表示这个格子周围雷的数量, 如果为 `-1` 则表示这个格子就是雷 

先声明一下:

```csharp
int mapRow = 10, mapColumn = 10, mineNum = 10;
int[,] map = new int[mapRow+1, mapColumn+1];
```

然后声明一下随机数要用的 `Random` 对象:

```csharp
Random rd = new Random();
```

然后循环访问随机位置, 把它设成雷:

```csharp
for(int cnt=1; cnt <= mineNum; ){ // cnt 表示正在放第 cnt 个雷, 注意这后面没写 cnt++
    int x = rd.Next(1, row+1); // 注意范围为左闭右开, 所以 row 需要加 1
    int y = rd.Next(1, col+1); 

    if(map[x, y] != -1){ // 不要重复放置雷, 那样雷的总数会少
        map[x, y] = -1;
        cnt++;
    }
}
```

接下来要访问整个棋盘, 数每个不是雷的格子周围的雷的数量, 代码:

```csharp
for(int row = 1; row <= mapRow; row++){ // 循环每行
    for(int col = 1; col <= mapColumn; col++){ // 循环每列
        if(map[row, col] != -1){ // 如果不是雷再计数
            // do something (见后文)
        }
    }
}
```

但在那之前, 我们要怎么遍历每个格子周围的 8 个格子?

其中一个方法是: 

由于每个格子相邻的格子的横纵坐标都是当前坐标加减 1, 所以我们可以用这样两个一维数组:

```csharp
int[] moveRow    = {  1,  1, 1, 0, -1, -1, -1,  0 }; // 加了一堆空格是为了便于理解
int[] moveColumn = { -1,  0, 1, 1,  1,  0, -1, -1 };
```

这样我们只要循环 `i`, 将当前的格子横纵坐标分别加上 `moveRow[i]` 和 `moveColumn[i]`, 就能遍历一个格子周围所有的位置了, 代码:
```csharp
int cnt = 0; // 用来记录周围雷的数量
for(int i=0; i < 8; i++){
    int currRow = row + moveRow[i]; // 新的行数
    int currCol = col + moveColumn[i]; // 新的列数

    // 如果找到的位置不在地图中就跳过
    if(currRow < 1 || currRow > mapRow || currCol < 1 || currCol > mapColumn) {continue;}
    
    if(map[currRow, currCol] == -1) { // 如果是雷就 +1
        cnt++;
    }
}
map[row, col] = cnt;
```

另一个方法不需要辅助数组, 再写一个二重循环, 判断一下不是本格就好:
```csharp
int cnt = 0; // 用来记录周围雷的数量
for(int i = -1; i <= 1; i++){
    for(int j = -1; j <= 1; j++){
        int currRow = row + i; // 新的行数
        int currCol = col + j; // 新的列数
    }

    // 如果找到的位置不在地图中就跳过
    if(currRow < 1 || currRow > mapRow || currCol < 1 || currCol > mapColumn) {continue;}

    // 如果就是本格也跳过
    if(currRow == row && currCol == col) {continue;}

    if(map[currRow, currCol] == -1) { // 如果是雷就 +1
        cnt++;
    }
}
map[row, col] = cnt;
```

最后把上面的代码组合起来, 加个输出, 完整代码如下:

{% hideToggle 完整代码 %}
```csharp
int mapRow = 10, mapColumn = 10, mineNum = 10;
int[,] map = new int[mapRow+1, mapColumn+1];

int[] moveRow = { 1, 1, 1, 0, -1, -1, -1, 0 };
int[] moveColumn = { -1, 0, 1, 1, 1, 0, -1, -1 };


Random rd = new Random();

for(int cnt=1; cnt <= mineNum; ){ // cnt 表示正在放第 cnt 个雷, 注意这后面没写 cnt++
    int x = rd.Next(1, mapRow+1); // 注意范围为左闭右开, 所以 row 需要加 1
    int y = rd.Next(1, mapColumn+1); 

    if(map[x, y] != -1){ // 不要重复放置雷, 那样雷的总数会少
        map[x, y] = -1;
        cnt++;
    }
}

for(int row = 1; row <= mapRow; row++){ // 循环每行
    for(int col = 1; col <= mapColumn; col++){ // 循环每列
        if(map[row, col] != -1){ // 如果不是雷再计数

            int cnt = 0; // 用来记录周围雷的数量
            for(int i=0; i < 8; i++){
                int currRow = row + moveRow[i]; // 新的行数
                int currCol = col + moveColumn[i]; // 新的列数

                // 如果找到的位置不在地图中就跳过
                if(currRow < 1 || currRow > mapRow || currCol < 1 || currCol > mapColumn) {continue;}
                
                if(map[currRow, currCol] == -1) { // 如果是雷就 +1
                    cnt++;
                }
            }
            map[row, col] = cnt;
        }
    }
}

for(int i=1; i <= mapRow; i++){
    for(int j=1; j <= mapColumn; j++){
        if(map[i, j] == -1) {
            Console.Write("* "); // 为了便于观察, 如果是雷就输出星号
        }
        else {
            Console.Write("{0} ", map[i, j]);
        }
    }
    Console.WriteLine(""); // 输出空行
}
```
{% endhideToggle %}

刚刚在我的电脑上产生的随机输出结果如下:
{% note default flat %}
```
0  0  0  0  0  2  *  2  0  0  
0  0  0  1  1  3  *  2  1  1
0  0  0  1  *  2  1  1  1  *
0  0  0  1  1  1  0  0  2  2
1  2  2  2  1  0  0  0  1  *
*  2  *  *  1  0  1  1  2  1
1  2  2  2  1  0  1  *  1  0
0  0  0  0  0  0  1  1  1  0
0  0  0  0  0  0  0  0  1  1
0  0  0  0  0  0  0  0  1  *
```
{% endnote %}

# 再谈字符串
字符串也可以用下标进行访问, 例如:
```csharp
string str = "abcde";
Console.WriteLine(str[0]);
```

字符串也有 `Length` 属性, 所以可以用 `str.Length` 访问：

```csharp
string str = "abcde";
for(int i=0; i < str.Length; i++){
    Console.WriteLine(str[i]);
}
```

当然也可以用 `foreach` 语句循环遍历字符串:
```csharp
string str = "abcde";
foreach(char c in str){
    Console.WriteLine(c);
}
```

但大家可能有些疑问，为什么是 `char c in str` 而不是 `string c`

因为字符串的本意就是一堆 "字符" 串起来, 也就是说, 字符串中的每一个元素应该是一个字符
`char` 就是表示字符的数据类型(英文character的缩写), 字符`a` 写为 `'a'`

因为 `'a'` (字符`a`)容易与 `"a"` (字符串`a`)混淆所以之前一直没有提过, 他们的区别就类似于int类型的 `5` 与 只有一个int类型的元素的数组 `{5}`, 是不一样的东西

## 例题 4-3 [洛谷[B2124](https://www.luogu.com.cn/problem/B2124)] 判断字符串是否为回文
输入一个字符串，输出该字符串是否回文。回文是指顺读和倒读都一样的字符串。
如果字符串是回文，输出 `yes` 否则，输出 `no`

```csharp
string str = Console.ReadLine();
int length = str.Length;
bool suc = true; 
for (int i = 0; i < length / 2; i++){
    if(str[i] != str[length-i-1]){
        suc = false;
        break;
    }
}

if(suc){
    Console.WriteLine("yes");
}
else{
    Console.WriteLine("no");
}
```

# 练习

## 4-1 [最高分与最低分之差](https://www.nowcoder.com/practice/e0e4f81dcd55408a8973f8033bbeb1d2?tpId=107&&tqId=33376&rp=1&ru=/ta/beginner-programmers&qru=/ta/beginner-programmers/question-ranking)
先读入 n , 下一行输入 n 个成绩，输出 n 个成绩中最高分数和最低分数的差。

## 4-2 [洛谷[B2122](https://www.luogu.com.cn/problem/B2122)] 单词翻转
小明同学写单词的时候喜欢反着写，比如 `hello` 他会写成 `olleh`
给出小明同学写的一个句子，请你将所有的单词复原。

### 输入 
共一行，一个字符串表示句子，单词之间以空格分隔。

### 输出 
每个单词一行

{% tabs 样例 %}
<!-- tab 样例输入 -->
olleh dlrow
<!-- endtab -->
<!-- tab 样例输出 -->
hello
world
<!-- endtab -->
{% endtabs %}

## 4-3 完善学生分数排名系统
接着完善一下学生分数排名的程序:
1. 本文给的代码只能处理整数, 改成能处理浮点数的
2. 对输入做一下判断, 例如: 如果输入的分数根本不能变为浮点数或者输入数字大于满分或者小于0, 就让它重新输入
3. 输出平均分数

{% hideToggle 提示 %}
1. 使用 Convert.ToDouble()
2. 可以用while循环 条件为输入正确
{% endhideToggle %}
