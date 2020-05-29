---
title: "文本处理"
date: 2020-05-19T21:16:14+08:00
slug: 11b451cb
draft: false
---

## 字母大写

```css
p { text-transform: uppercase; }
```

## 文本省略

一行的多余文字省略

```css
div {
    border: 1px solid red;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
}
```

多行的多余文字省略（在第二行后加省略，第二行后的内容会被隐藏）：

```css
div {
    border: 1px solid red;
    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
    overflow: hidden;
}
```

更多方法，谷歌搜索：`css multiline text ellipsis`

更多文本样式教程：https://css-tricks.com/line-clampin/

## 文本字符

```html
空格符：&nbsp;
```

## 禁止文本选中

```css
p {
    -moz-user-select:none; /*火狐*/
    -webkit-user-select:none; /*webkit浏览器*/
    -ms-user-select:none; /*IE10*/
    -khtml-user-select:none; /*早期浏览器*/
    user-select:none;
}
```

## 两边对齐

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <title>JS Bin</title>
    <style>
        span {
            border: 1px solid green;
            display: inline-block;
            width: 5em;
            text-align: justify;
            line-height: 20px;
            overflow: hidden;
            height: 20px;
        }
        span::after {
            content: '';
            display: inline-block;
            width: 100%;
            border: 1px solid blue;
        }
    </style>
</head>
<body> 
    <span>姓名</span><br data-tomark-pass> 
    <span>联系电话</span>
</body>
</html>
```

> 原理：首先将span标签添加为行内块元素并添加 text-align: justify; 属性，此属性表示多行文字内容左右占满对齐，但此时span只有一行，所以需要用伪元素添加多行，给span 添加一个 after 伪元素使它和span本身的宽度一样宽，由于上面设置的宽度是5em，所以after就沾满了，此时span的宽度才被撑开到5em，此时就是左右文字都填充对齐了，再给span一个相同的高度和行高 并且使用 overflow: hidden 隐藏多余的after伪元素，就可以了

## 内联元素

### 连续字母换行

有时多个连续的英文字母即时用内联元素包裹也无法换行，如下案例所示：
代码

```html
<style>
    div {
        width: 200px;
        height: 50px;
        border: 1px solid blue;
    }
</style>
<div>
    <span>ssssssssssssssssssaaaaaaaaaa</span>
</div>
```

效果链接：http://js.jirengu.com/cugovewodi/2/edit

这时给div添加以下属性

```css
div { word-break: break-all; }
```

连续字母就可以换行了
效果链接：http://js.jirengu.com/hehatujuwe/1/edit

### 解决定位时内联元素竖直排列

当一个内联元素绝对定位时，会竖直排列，而不是正常横向排列给内联元素添加以下属性即可

```css
white-space: nowrap;
```

## pre 标签自动换行

```css
pre{white-space:pre-wrap;white-space:-moz-pre-wrap;white-space:-pre-wrap;white-space:-o-pre-wrap;word-wrap:break-word;}
```