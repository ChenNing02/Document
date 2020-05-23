---
title: JSON 是什么？
---



# JSON 是什么？

（本文精髓在最后一节）

JSON 绝对不是对象，请问

1. JSON 是什么？
2. "null" 是 JSON 吗？"1" 是 JSON 吗？
3. JSON 与 JS 对象的区别是什么？

## JSON 是什么？

如果你在 Google 搜索 JSON，那么一眼就会看到 JSON 的官网 [http://json.org](https://link.zhihu.com/?target=http%3A//json.org)。

官网会明明白白的告诉你，JSON 是一种数据格式。

什么是格式？你可以理解为语法。JSON 的格式灵感来自于 JS 对象字面量的语法，但是两者没有任何关联。

这种格式可以描述三种数据。

**1. object（无序的「键-值」集合）。**

语法如下：



![img](https://pic1.zhimg.com/80/v2-f3506a958146d1338ed7fb0482a9a7dc_hd.png)

这个图叫做语法图，你可以讲其想象成铁轨，有一列火车从左往右行驶。

这列火车遇到的第一个符号是 { ，所以对象语法的第一个符号也必须是 { 。

如果继续直行，会分别遇到 string、冒号和 value，所以对应的文本内容是 { string: value 。

然后你可以选择直行或者往下拐，最后到达终点。

把旅途中遇到的所有符号连起来，就是完整的语法。

比如下面三种写法都可以表示 object

```text
{}
{"key1": "value1"} // string 对应 "key1"，value 对应 "value1"，后面会讲
{"key1": "value1", "key2": "value2"}
```

**2. array（有序的值集合）**

语法如下：



![img](https://pic2.zhimg.com/80/v2-eecf273d0d2f2112acb842af6d3a6371_hd.png)

下面三种写法都可以表示 array

```text
[]
[1]
[1,"hi"]
```

**3. value**



![img](https://pic2.zhimg.com/80/v2-999977039ab20b141c2a0ba71fec6035_hd.png)

value 对应对象语法图里的 value 和数组语法图里 value，value 也可以是 object 或 array，所以下面的语法成立：

```text
{"key1": { "key2" : "value2" } }
[ 1, [ 2, 3 ] ]
```

另外值还可以是 string、number、true、false 和 null。

**string 的语法如下：**



![img](https://pic4.zhimg.com/80/v2-d522adbd6698b92a4d1f8b0b87e81e27_hd.png)

你可能奇怪为什么 string 的语法这么复杂，我举例来说明你就明白了：

```text
"你好"
"\"你好\""
"\\你好\\"
"\/你好\/"
"\b\f\n\r\t特殊符号"
"\u4f60用编码表示字符"
```

上面都是合法的 string。这也是「JSON 中字符串必须使用双引号」的原因——规定如此。

number 的语法如下，有兴趣可以自己走一遍：



![img](https://pic2.zhimg.com/80/v2-7d65ad2e9ddacf063d3cc1b1ca9a6f9d_hd.png)

**另外需要特殊提醒一下，true、false 和 null 都是合法的 JSON。**

## JSON 和 JS Object 的区别

简单来说，两种没有任何关联。

JSON 语法的作者是道格拉斯（Douglas Crockford），JS 语法的作者是布兰登・艾奇（Brendan Eich）。道格拉斯发明 JSON 的时候参考了 JS 的对象语法，仅此而已。

如果硬要说区别：

\1. JSON 的字符串必须用双引号。

\2. JSON 无法表示 undefined，只能表示 "undefined"

\3. JSON 无法表示函数

\4. JSON 的对象语法不能有引用



以上，就是对 JSON 的详细介绍。

欢迎进群与我探讨技术，暗号：前端/Java交流（附二维码）[http://qr.jirengu.com/api/taskUrl?tid=56](https://link.zhihu.com/?target=http%3A//qr.jirengu.com/api/taskUrl%3Ftid%3D56)

编辑于 2019-07-17

***

> 本文转自：https://zhuanlan.zhihu.com/p/22627657?refer=study-fe