```csharp
using System;

for(int i=1; ; i++) {
    int n = i * i;
    if (n < 1000) continue;
    if (n > 9999) break;

    int aa = n / 100; // 取前2位数字
    int bb = n % 100; // 取后2位数字
    if (aa / 10 == aa % 10 && bb / 10 == bb % 10) Console.WriteLine(n);
}
```
