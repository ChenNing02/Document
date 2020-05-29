---
title: "布局案例"
date: 2020-05-19T21:37:18+08:00
slug: 7ff95c3e
draft: false
---

## 1. [左　右右]

使用 flex布局 中的 `justify-content: space-between;` 加 `margin-left: auto;` 实现

效果：

![示例](https://chenning02.github.io/Document/blog-img/css-flex_li02.jpg)

代码：

html

```html
<div class="parent">
    <div class="item1 block"></div>
    <div class="item2 block"></div>
    <div class="item3 block"></div>
</div>
```

css

```css
.parent {
    display: flex;
    justify-content: space-between;
    background-color: #dddddd;
    padding:5px;
}
.block {
    width: 100px;
    height: 100px;
    background-color: #e88024;
}
.item2 {
    margin-left: auto;
    background-color: #89479b;
}
```