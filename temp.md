## 1-2 直角三角形
```csharp
int a = Convert.ToInt32(Console.ReadLine());
int b = Convert.ToInt32(Console.ReadLine());
int c = Convert.ToInt32(Console.ReadLine());

if(a*a == b*b + c*c || b*b == a*a + c*c || c*c == a*a + b*b) {
    Console.WriteLine("yes");
} 
else {
    Console.WriteLine("no");
}
```

{% note info flat %}
如果你不知道哪个运算符的优先级比较高, 那就多加括号
{% endnote %}

### 1-2-2
```csharp
if(a + b <= c && a + c <= b || b + c <= a) {
    Console.WriteLine("not a triangle");
} 
else {
    if(a*a == b*b + c*c || b*b == a*a + c*c || c*c == a*a + b*b) {
        Console.WriteLine("yes");
    } 
    else {
        Console.WriteLine("no");
    }				
}	
```

## 1-3 三排序
```csharp
int a = Convert.ToInt32(Console.ReadLine());
int b = Convert.ToInt32(Console.ReadLine());
int c = Convert.ToInt32(Console.ReadLine());

if(a > b){
    int temp = a;
    a = b;
    b = temp;
}
if(a > c){
    int temp = a;
    a = c;
    c = temp;
}
if(b > c){
    int temp = b;
    b = c;
    c = temp;
}

Console.WriteLine("{0}\n{1}\n{2}", a, b, c);
```

## 1-4 一元二次方程

```csharp
int a = Convert.ToInt32(Console.ReadLine());
int b = Convert.ToInt32(Console.ReadLine());
int c = Convert.ToInt32(Console.ReadLine());

double delta = b * b - 4 * a * c;

if(delta < 0) {
Console.WriteLine("No Answer");
}
else {
Console.WriteLine("{0:F2}", (- b - Math.Sqrt(delta))/2/a);
}

if(delta > 0){
Console.WriteLine("{0:F2}", (- b + Math.Sqrt(delta))/2/a);
}
```