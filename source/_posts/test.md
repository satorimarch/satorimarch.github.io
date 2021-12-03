---
title: test
abbrlink: 63534
date: 2021-11-28 00:00:00
---

# 一级标题

## 二级标题

### 三级标题

#### 四级标题

##### 五级标题

###### 六级标题

> 提示块标签
>
>> 嵌套提示块
>>

- 无序列表1
- 无序列表2

1. 有序列表1
2. 有序列表2

__加粗__，*斜体*，~~删除线~~，<u>下划线</u>。


```c++
printf("hello world");
```

```c++
cout << "hello world";
```

```java
System.out.println("hello world");
```

```csharp
Console.WriteLine("hello world");
```

$$
F=ma
$$

$$
\sum_{i=0}^{n}a_i
$$

试试行内公式: $f^{\prime}(x) = 2x^{2}$

[^这是脚注]

这也是脚注[^1]

---

> 以下部分的[详细使用方法](https://butterfly.js.org/posts/4aa8abbe/#%E6%A8%99%E7%B1%A4%E5%A4%96%E6%8E%9B%EF%BC%88Tag-Plugins%EF%BC%89)

{% label 这是红色 red %}

{% label 这是粉色 pink %}

{% label 这是橙色 orange %}

{% label 这是黄色 yellow %}

{% label 这是蓝色 blue %}

{% label 这是绿色 green %}

{% label 这是紫色 purple %}

{% label 这是灰色 %}

---

{% note 'fab fa-cc-visa' flat %}
你是刷 Visa 还是 UnionPay
{% endnote %}
{% note blue 'fas fa-bullhorn' flat %}
2021年快到了....
{% endnote %}
{% note pink 'fas fa-car-crash' flat %}
小心开车 安全至上
{% endnote %}
{% note red 'fas fa-fan' flat%}
这是三片呢？还是四片？
{% endnote %}
{% note orange 'fas fa-battery-half' flat %}
你是刷 Visa 还是 UnionPay
{% endnote %}
{% note purple 'far fa-hand-scissors' flat %}
剪刀石头布
{% endnote %}
{% note green 'fab fa-internet-explorer' flat %}
前端最讨厌的浏览器
{% endnote %}

---

{% note flat %}
默认 提示块标签
{% endnote %}

{% note default flat %}
default 提示块标签
{% endnote %}

{% note primary flat %}
primary 提示块标签
{% endnote %}

{% note success flat %}
success 提示块标签
{% endnote %}

{% note info flat %}
info 提示块标签
{% endnote %}

{% note warning flat %}
warning 提示块标签
{% endnote %}

{% note danger flat %}
danger 提示块标签
{% endnote %}

{% btn 'https://butterfly.js.org/',Butterfly,far fa-hand-point-right,larger %}
{% btn 'https://butterfly.js.org/',Butterfly,far fa-hand-point-right,blue larger %}
{% btn 'https://butterfly.js.org/',Butterfly,far fa-hand-point-right,pink larger %}
{% btn 'https://butterfly.js.org/',Butterfly,far fa-hand-point-right,red larger %}
{% btn 'https://butterfly.js.org/',Butterfly,far fa-hand-point-right,purple larger %}
{% btn 'https://butterfly.js.org/',Butterfly,far fa-hand-point-right,orange larger %}
{% btn 'https://butterfly.js.org/',Butterfly,far fa-hand-point-right,green larger %}



{% tabs test1 %}
<!-- tab -->
**This is Tab 1.**
<!-- endtab -->

<!-- tab -->
**This is Tab 2.**
<!-- endtab -->

<!-- tab -->
**This is Tab 3.**
<!-- endtab -->
{% endtabs %}



{% tabs test4 %}
<!-- tab 第一個Tab -->
**tab名字為第一個Tab**
<!-- endtab -->

<!-- tab @fab fa-apple-pay -->
**只有圖標 沒有Tab名字**
<!-- endtab -->

<!-- tab 炸彈@fas fa-bomb -->
**名字+icon**
<!-- endtab -->
{% endtabs %}

---

> 以下部分修改自这个人的 `typora` 主题的[demo](https://typora-dyzj-theme.vercel.app/#ref-footnote-1)

<kbd>ctrl</kbd>键


可以通过设置 `background-color`属性控制背景色，如：`<font style="background-color:#8bc34a">`绿色小标签`</font>`

<div alt="three-table"> <!--alt还可取值为"notitle-table"，一种无表头的小型表格-->
<table>
  <tr>
    <th alt="left">标题1</th>
    <th alt="center">标题2</th>
    <th alt="right">标题3</th>
  </tr>
  <tr>
    <td alt="left">居左：alt="left"</td>
    <td alt="center">居中：alt="center"</td>
    <td alt="right">居右：alt="right"</td>
  </tr>
  <tr>
    <td alt="left">x</td>
    <td alt="center">y</td>
    <td alt="right">z</td>
  </tr>
</table>
</div>

<div alt="fig">表1.    三线表</div>

[跳转](#二级标题)至指定标题（锚点），也可以在任意位置通过 `<a name="锚点名" alt="none"> </a>`（为了方便编辑，typora会显示空标签或 `style="display:none"`的标签，但填充一个空格就可以被隐藏，在导出为HTML文件时，由于该款超链接样式有一个padding宽度，所以空链接还是会显示下划线，`alt="none"`用于避免该问题，如果自定义的锚点有文字说明，则不要使用 `alt="none"`）设定锚点，示例：[求点个赞呗](#star)

<a href="#" alt="null">无样式链接</a>，主要用于图片超链接，如：<a href="#" alt="null"><img src="https://img.shields.io/badge/-GitHub-181717?style=flat-square&logo=github"><img src="https://img.shields.io/badge/-Git-F05032?style=flat-square&logo=git&logoColor=white"></a>

<ruby>Base<rp> (</rp><rt>top</rt><rp>) </rp></ruby>、<ruby>佐天泪子<rp> (</rp><rt>xiān qún kuáng mó</rt><rp>) </rp></ruby>、<ruby>超電磁砲<rp> (</rp><rt>レールガン</rt><rp>) </rp></ruby>


<audio controls="controls">
  <source src="/music/parsley.mp3" type="audio/mp3" />
</audio>

> 可以将 `<audio>`音频包裹在 `<center></center>`中居中显示

插入网易云的外链播放器（`<iframe>`，可嵌入油管等平台视频）：

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=330 height=86 src="https://music.163.com/outchain/player?type=2&id=1836421270&auto=1&height=66"></iframe>

<details>
    <summary>折叠标签</summary>
    青青子衿，悠悠我心
</details>
> 关于Typora对HTML的支持说明：<https://support.typora.io/HTML/>

[Emoji表情符号](https://www.webfx.com/tools/emoji-cheat-sheet/)：😄（`:smile:`），Decimal NCRs或Hexadecimal NCRs^[2]^编码也是受支持的，譬如“笑哭”：&#128514;（`&#128514;`）或&#x1F602;（`&#x1F602;`）

<center><svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1" height="400px" viewBox="-0.5 -0.5 1071 773" content="<mxfile host="app.diagrams.net" modified="2021-11-15T07:08:52.373Z" agent="5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/86.0.4240.198 Safari/537.36" etag="aOnjZZMrixLFimZz001-" version="15.7.3" type="google"><diagram id="07fea595-8f29-1299-0266-81d95cde20df" name="Page-1">7Zpdk5o8FMc/jZfrkDeEy3Xdtjed6cx25rnOIylmisbGuGI/fQMEAZN1sY2uW+qNchKS8P9xPOcERuhhmX+UdL34LBKWjWCQ5CM0G0F4F4NQfxWWvbGEpDKkkieVCTSGJ/6TGWNgrFuesE2noxIiU3zdNc7FasXmqmOjUopdt9s3kXVnXdOUWYanOc1s6388UQtjBWHcNHxiPF2YqSM4qRr+p/PvqRTblZlvJVasalnSehhzjZsFTcSuZUKPI/QghVDVr2X+wLJC1lqx6rwPL7QelizZSvU5YQJRdcozzbbmus3K1L4WYrfgij2t6bw43mnYIzT9xrPsQWRCll0QgPf3U6LtqaQJ15PXbeW1N+YZlxoVFyvdxOhGr3G6UVJ8Z0f9F2qZ6SNQzCSa0fRMEGFM9Oqn9qWaq39mUrG8ZTKX/pGJJVNyr7uYVojjydjclOYmBTjEYxI0HyPHrnUH1PAWLfgAGSM1d116mK2RX/8wBF6igYdMI7RpEIxr02sESDAO2tyQDx5kyDwih3fEvXmAwItHhAMmgAIHAdifwMQLgcnrBFiiI6c5fFWhyj8PytaxFVlat/u+qGYx9Ukt2yoFp+5TyTKq+HM3+rukM3N8EVyvpRVMkP331bhLPdBGbOWcmXPbkbnHcABYwykqU6as4UqqBxF6go68uNqHIJoE787VXKkAQm+ZCsReaDxGJMTwb6ABgy6Nvn+CXmjUgwzTNxyJGYrwGMfNJ+pJg8TjuH2ajywNAS9w3qmruOCQ3jmCH++AQ/YOR5pcRo6eHhF6IeCnjH+nLuAgAPq7AIi8EOhRuv9Lk72nyQiRPsN5TJORvSfwhUqqh2CyXNcxdX0Xlw6iPY+v0q9C+93sjtjszQ4oiOpjM0TBdV2svLwWMh2R2Uv+5sGZEAptQSPocKbIcZdAL65k1/w56C8rzXha/DHNtQgaCZoWF8/nNLs3DUueJMUolsongFwPgCv3JXF43YBu1/y5/Xf21xJwbURem4BdjOdoOAQcEf3qBPwU4O905xFaYTV2bv0i0tl1BwC7cHR35usdxT/Cg4dckZd42uX3ESrSLc7jG8I25Frd5VXAk1cd+vwZHruS/7pfM205IwFriWmHjHZQIb5ktaJFDOLOZiGwJL5Y9ortUtxIeEYGdQsSkreT0K6ljYRnpEC3IGH8dhKerlL3v6XjuVWqh0QQ2YlgEJFrVqPYrkb3t1aN+qg6A3Is9OuvwiDXRhHsbvFPvKQNdkG6v7WC9DIQ3FvJ1xPerkP3t1aHXkb48nnjGwrvKj/DTBk9OvqHP7aibrjblErdF8EyWOdlbKvb9a+0+J5xqhPkpe6iuNJjmHH1mqqhq14Xo1yhRMERdXA6aPugbG09R87HBBFwUMbEA1Uy6KrV8ToTmpzxgp8PAIOuPx0AYNj/QRnwQsAuMXN8YxHlgo9XHAguu7OpD5v3yasHXs37+ujxFw==</diagram></mxfile>" onclick="(function(svg){var src=window.event.target||window.event.srcElement;while (src!=null&&src.nodeName.toLowerCase()!='a'){src=src.parentNode;}if(src==null){if(svg.wnd!=null&&!svg.wnd.closed){svg.wnd.focus();}else{var r=function(evt){if(evt.data=='ready'&&evt.source==svg.wnd){svg.wnd.postMessage(decodeURIComponent(svg.getAttribute('content')),'*');window.removeEventListener('message',r);}};window.addEventListener('message',r);svg.wnd=window.open('https://viewer.diagrams.net/?client=1&page=0&edit=_blank');}}})(this);" style="cursor:pointer;max-width:100%;max-height:773px;"><defs/><g><rect x="100.5" y="610.5" width="120" height="130" fill="#12aab5" stroke="none" pointer-events="all"/><rect x="300.5" y="690.5" width="120" height="50" fill="#12aab5" stroke="none" pointer-events="all"/><rect x="500.5" y="640.5" width="120" height="100" fill="#12aab5" stroke="none" pointer-events="all"/><rect x="700.5" y="570.5" width="120" height="170" fill="#12aab5" stroke="none" pointer-events="all"/><path d="M 40.5 740.5 L 40.5 270.6" fill="none" stroke="#000000" stroke-width="3" stroke-miterlimit="10" pointer-events="stroke"/><path d="M 40.5 263.85 L 45 272.85 L 40.5 270.6 L 36 272.85 Z" fill="#000000" stroke="#000000" stroke-width="3" stroke-miterlimit="10" pointer-events="all"/><rect x="100.5" y="480.5" width="120" height="130" fill="#f08705" stroke="none" pointer-events="all"/><rect x="100.5" y="350.5" width="120" height="130" fill="#e85642" stroke="none" pointer-events="all"/><rect x="300.5" y="530.5" width="120" height="160" fill="#f08705" stroke="none" pointer-events="all"/><rect x="300.5" y="500.5" width="120" height="30" fill="#e85642" stroke="none" pointer-events="all"/><rect x="500.5" y="480.5" width="120" height="160" fill="#f08705" stroke="none" pointer-events="all"/><rect x="500.5" y="300.5" width="120" height="180" fill="#e85642" stroke="none" pointer-events="all"/><path d="M 40.5 740.5 L 950.4 740.5" fill="none" stroke="#000000" stroke-width="3" stroke-miterlimit="10" pointer-events="stroke"/><path d="M 957.15 740.5 L 948.15 745 L 950.4 740.5 L 948.15 736 Z" fill="#000000" stroke="#000000" stroke-width="3" stroke-miterlimit="10" pointer-events="all"/><rect x="970.5" y="728.5" width="80" height="20" fill="none" stroke="none" pointer-events="all"/><g transform="translate(-0.5 -0.5)"><switch><foreignObject pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility" style="overflow: visible; text-align: left;"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe flex-start; justify-content: unsafe flex-start; width: 1px; height: 1px; padding-top: 731px; margin-left: 973px;"><div data-drawio-colors="color: rgba(0, 0, 0, 1); " style="box-sizing: border-box; font-size: 0px; text-align: left;"><div style="display: inline-block; font-size: 18px; font-family: Helvetica; color: rgb(0, 0, 0); line-height: 1.2; pointer-events: all; white-space: nowrap;">Parameter x</div></div></div></foreignObject><text x="973" y="749" fill="rgba(0, 0, 0, 1)" font-family="Helvetica" font-size="18px">Parameter...</text></switch></g><rect x="100.5" y="742.5" width="120" height="30" fill="none" stroke="none" pointer-events="all"/><g transform="translate(-0.5 -0.5)"><switch><foreignObject pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility" style="overflow: visible; text-align: left;"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 1px; height: 1px; padding-top: 755px; margin-left: 161px;"><div data-drawio-colors="color: rgba(0, 0, 0, 1); " style="box-sizing: border-box; font-size: 0px; text-align: center;"><div style="display: inline-block; font-size: 18px; font-family: Helvetica; color: rgb(0, 0, 0); line-height: 1.2; pointer-events: all; white-space: nowrap;">x1</div></div></div></foreignObject><text x="161" y="760" fill="rgba(0, 0, 0, 1)" font-family="Helvetica" font-size="18px" text-anchor="middle">x1</text></switch></g><rect x="300.5" y="742.5" width="120" height="30" fill="none" stroke="none" pointer-events="all"/><g transform="translate(-0.5 -0.5)"><switch><foreignObject pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility" style="overflow: visible; text-align: left;"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 1px; height: 1px; padding-top: 755px; margin-left: 361px;"><div data-drawio-colors="color: rgba(0, 0, 0, 1); " style="box-sizing: border-box; font-size: 0px; text-align: center;"><div style="display: inline-block; font-size: 18px; font-family: Helvetica; color: rgb(0, 0, 0); line-height: 1.2; pointer-events: all; white-space: nowrap;">x2</div></div></div></foreignObject><text x="361" y="760" fill="rgba(0, 0, 0, 1)" font-family="Helvetica" font-size="18px" text-anchor="middle">x2</text></switch></g><rect x="500.5" y="742.5" width="120" height="30" fill="none" stroke="none" pointer-events="all"/><g transform="translate(-0.5 -0.5)"><switch><foreignObject pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility" style="overflow: visible; text-align: left;"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 1px; height: 1px; padding-top: 755px; margin-left: 561px;"><div data-drawio-colors="color: rgba(0, 0, 0, 1); " style="box-sizing: border-box; font-size: 0px; text-align: center;"><div style="display: inline-block; font-size: 18px; font-family: Helvetica; color: rgb(0, 0, 0); line-height: 1.2; pointer-events: all; white-space: nowrap;">x3</div></div></div></foreignObject><text x="561" y="760" fill="rgba(0, 0, 0, 1)" font-family="Helvetica" font-size="18px" text-anchor="middle">x3</text></switch></g><rect x="860.5" y="140.5" width="35" height="30" fill="#12aab5" stroke="none" pointer-events="all"/><rect x="860.5" y="100.5" width="35" height="30" fill="#f08705" stroke="none" pointer-events="all"/><rect x="860.5" y="60.5" width="35" height="30" fill="#e85642" stroke="none" pointer-events="all"/><rect x="900.5" y="65.5" width="80" height="20" fill="none" stroke="none" pointer-events="all"/><g transform="translate(-0.5 -0.5)"><switch><foreignObject pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility" style="overflow: visible; text-align: left;"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe flex-start; justify-content: unsafe flex-start; width: 1px; height: 1px; padding-top: 68px; margin-left: 903px;"><div data-drawio-colors="color: rgba(0, 0, 0, 1); " style="box-sizing: border-box; font-size: 0px; text-align: left;"><div style="display: inline-block; font-size: 15px; font-family: Helvetica; color: rgb(0, 0, 0); line-height: 1.2; pointer-events: all; white-space: nowrap;">Type 1</div></div></div></foreignObject><text x="903" y="83" fill="rgba(0, 0, 0, 1)" font-family="Helvetica" font-size="15px">Type 1</text></switch></g><rect x="900.5" y="105.5" width="80" height="20" fill="none" stroke="none" pointer-events="all"/><g transform="translate(-0.5 -0.5)"><switch><foreignObject pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility" style="overflow: visible; text-align: left;"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe flex-start; justify-content: unsafe flex-start; width: 1px; height: 1px; padding-top: 108px; margin-left: 903px;"><div data-drawio-colors="color: rgba(0, 0, 0, 1); " style="box-sizing: border-box; font-size: 0px; text-align: left;"><div style="display: inline-block; font-size: 15px; font-family: Helvetica; color: rgb(0, 0, 0); line-height: 1.2; pointer-events: all; white-space: nowrap;">Type 2</div></div></div></foreignObject><text x="903" y="123" fill="rgba(0, 0, 0, 1)" font-family="Helvetica" font-size="15px">Type 2</text></switch></g><rect x="900.5" y="145.5" width="80" height="20" fill="none" stroke="none" pointer-events="all"/><g transform="translate(-0.5 -0.5)"><switch><foreignObject pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility" style="overflow: visible; text-align: left;"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe flex-start; justify-content: unsafe flex-start; width: 1px; height: 1px; padding-top: 148px; margin-left: 903px;"><div data-drawio-colors="color: rgba(0, 0, 0, 1); " style="box-sizing: border-box; font-size: 0px; text-align: left;"><div style="display: inline-block; font-size: 15px; font-family: Helvetica; color: rgb(0, 0, 0); line-height: 1.2; pointer-events: all; white-space: nowrap;">Type 3</div></div></div></foreignObject><text x="903" y="163" fill="rgba(0, 0, 0, 1)" font-family="Helvetica" font-size="15px">Type 3</text></switch></g><rect x="0.5" y="231.5" width="80" height="20" fill="none" stroke="none" pointer-events="all"/><g transform="translate(-0.5 -0.5)"><switch><foreignObject pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility" style="overflow: visible; text-align: left;"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe flex-start; justify-content: unsafe flex-start; width: 1px; height: 1px; padding-top: 234px; margin-left: 3px;"><div data-drawio-colors="color: rgba(0, 0, 0, 1); " style="box-sizing: border-box; font-size: 0px; text-align: left;"><div style="display: inline-block; font-size: 18px; font-family: Helvetica; color: rgb(0, 0, 0); line-height: 1.2; pointer-events: all; white-space: nowrap;">Parameter y</div></div></div></foreignObject><text x="3" y="252" fill="rgba(0, 0, 0, 1)" font-family="Helvetica" font-size="18px">Parameter...</text></switch></g><rect x="8.5" y="610.5" width="30" height="130" fill="none" stroke="none" pointer-events="all"/><g transform="translate(-0.5 -0.5)"><switch><foreignObject pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility" style="overflow: visible; text-align: left;"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 1px; height: 1px; padding-top: 673px; margin-left: 24px;"><div data-drawio-colors="color: rgba(0, 0, 0, 1); " style="box-sizing: border-box; font-size: 0px; text-align: center;"><div style="display: inline-block; font-size: 18px; font-family: Helvetica; color: rgb(0, 0, 0); line-height: 1.2; pointer-events: all; white-space: nowrap;">y1</div></div></div></foreignObject><text x="24" y="678" fill="rgba(0, 0, 0, 1)" font-family="Helvetica" font-size="18px" text-anchor="middle">y1</text></switch></g><rect x="8.5" y="480.5" width="30" height="130" fill="none" stroke="none" pointer-events="all"/><g transform="translate(-0.5 -0.5)"><switch><foreignObject pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility" style="overflow: visible; text-align: left;"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 1px; height: 1px; padding-top: 543px; margin-left: 24px;"><div data-drawio-colors="color: rgba(0, 0, 0, 1); " style="box-sizing: border-box; font-size: 0px; text-align: center;"><div style="display: inline-block; font-size: 18px; font-family: Helvetica; color: rgb(0, 0, 0); line-height: 1.2; pointer-events: all; white-space: nowrap;">y2</div></div></div></foreignObject><text x="24" y="548" fill="rgba(0, 0, 0, 1)" font-family="Helvetica" font-size="18px" text-anchor="middle">y2</text></switch></g><rect x="8.5" y="350.5" width="30" height="130" fill="none" stroke="none" pointer-events="all"/><g transform="translate(-0.5 -0.5)"><switch><foreignObject pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility" style="overflow: visible; text-align: left;"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 1px; height: 1px; padding-top: 413px; margin-left: 24px;"><div data-drawio-colors="color: rgba(0, 0, 0, 1); " style="box-sizing: border-box; font-size: 0px; text-align: center;"><div style="display: inline-block; font-size: 18px; font-family: Helvetica; color: rgb(0, 0, 0); line-height: 1.2; pointer-events: all; white-space: nowrap;">y3</div></div></div></foreignObject><text x="24" y="418" fill="rgba(0, 0, 0, 1)" font-family="Helvetica" font-size="18px" text-anchor="middle">y3</text></switch></g><rect x="40.5" y="0.5" width="810" height="45" fill="none" stroke="none" pointer-events="all"/><g transform="translate(-0.5 -0.5)"><switch><foreignObject pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility" style="overflow: visible; text-align: left;"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 1px; height: 1px; padding-top: 21px; margin-left: 446px;"><div data-drawio-colors="color: rgba(0, 0, 0, 1); " style="box-sizing: border-box; font-size: 0px; text-align: center;"><div style="display: inline-block; font-size: 30px; font-family: Helvetica; color: rgb(0, 0, 0); line-height: 1.2; pointer-events: all; font-weight: bold; white-space: nowrap;"><font style="font-size: 30px">Diagram title</font></div></div></div></foreignObject><text x="446" y="30" fill="rgba(0, 0, 0, 1)" font-family="Helvetica" font-size="30px" text-anchor="middle" font-weight="bold">Diagram title</text></switch></g><rect x="700.5" y="520.5" width="120" height="50" fill="#f08705" stroke="none" pointer-events="all"/><rect x="700.5" y="410.5" width="120" height="110" fill="#e85642" stroke="none" pointer-events="all"/><rect x="700.5" y="742.5" width="120" height="30" fill="none" stroke="none" pointer-events="all"/><g transform="translate(-0.5 -0.5)"><switch><foreignObject pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility" style="overflow: visible; text-align: left;"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 1px; height: 1px; padding-top: 755px; margin-left: 761px;"><div data-drawio-colors="color: rgba(0, 0, 0, 1); " style="box-sizing: border-box; font-size: 0px; text-align: center;"><div style="display: inline-block; font-size: 18px; font-family: Helvetica; color: rgb(0, 0, 0); line-height: 1.2; pointer-events: all; white-space: nowrap;">x4</div></div></div></foreignObject><text x="761" y="760" fill="rgba(0, 0, 0, 1)" font-family="Helvetica" font-size="18px" text-anchor="middle">x4</text></switch></g></g><switch><g requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility"/><a transform="translate(0,-5)" xlink:href="https://www.diagrams.net/doc/faq/svg-export-text-problems" target="_blank"><text text-anchor="middle" font-size="10px" x="50%" y="100%">Viewer does not support full SVG 1.1</text></a></switch></svg></center>

<div alt="fig">图2.    柱状图</div>

[在线编辑地址](https://app.diagrams.net/?src=about#G1XbVy9iD3kEJMiCqG2IceUlNBIzMbcJYS)，该图表由[drawio](https://www.diagrams.net/)提供支持（提供iframe嵌入代码和svg嵌入代码），还支持UML类图、Network网络拓扑图、Flowcharts流程图、Tables表格等众多图表类型

---

[^1]: 这是脚注1

[^这是脚注]: 我是一个脚注
