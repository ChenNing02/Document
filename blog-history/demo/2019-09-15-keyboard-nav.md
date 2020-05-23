---
weight: 1
title: 键盘导航
date: 2019-09-15 22:53:55
---

## 键盘导航

案例预览：xxx

代码链接：xxx

## 使用的API

### Element

**创建标签**

```js
element = document.createElement('div')
```

**追加到布局中**

```js
element.appendChild(divs)
```

**在元素中追加文本**

```js
element.textContent = "Hi"
```

**给元素设置class样式**

```js
element.className = 'demo'
```

**监听整个文档的键盘事件**

```js
element.onkeypress = event handling code
// 实例
document.onkeypress = function(x){
	console.log(x)
}
```

**获取当前事件的元素**

```js
element.onclick = function(e){
	console.log(e.target)  // e.target 即当前元素
}
```

**获取上一个兄弟节点**

```
element.previousSibling
```

### 浏览器地址

**修改浏览器当前地址栏的地址**

```js
location.href = 'http://xxx.com'
```

**在新窗口打开地址**

```js
window.open('http://xxx.com', '_blank')
```

语法

```js
window.open(地址, 打开方式)
```

### LocalStorage

在 `localStorage` 中存储一个哈希

```js
let keyValue = JSON.stringify(hash) //存储的值需要转换

localStorage.setItem(keyName, keyValue)
```

在 `localStorage` 中读取一个哈希

```js
localStorage.getItem(keyName); // 通过名称获取值
```

> `getItem()`表示根据键名返回键的值

### JSON

**解析 JSON 格式的字符串**

```js
JSON.parse()
```

案例：

```js
var json = '{"result":true, "count":42}';
obj = JSON.parse(json);
```

**将一个JavaScript值 (对象或者数组) 转换为一个 JSON字符串**

```js
JSON.stringify(value) // value 表示 JavaScript值 (对象或者数组)
```

### 事件错误处理函数

`error` 事件的[事件处理程序](https://developer.mozilla.org/zh-CN/docs/Web/Guide/Events/Event_handlers)。针对各种目标的不同类型的错误触发了 Error 事件：

当一项资源（如`img` 或 `script`）**加载失败**，加载资源的元素会触发一个[`Event`](https://developer.mozilla.org/zh-CN/docs/Web/API/Event)接口的`error`事件，并执行该元素上的`onerror()`处理函数。这些error事件不会向上冒泡到window，不过（至少在Firefox中）能被单一的[`window.addEventListener`](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/addEventListener)捕获。

案例：

```js
img.onerror = function(e){
	e.target.src = 'images.png'
} // 当获取图片的值错误时则执行 onerror 后的函数
```

## 封装函数

**创建元素**

```js
function tag(tagName){
    return document.createElement(tagName)
}
```

**创建元素并添加属性**

```js
function tag(tagName, attributes){
	let element = document.createElement(tagName)
    for(let key in attributes){
        element[key] = attributes[key]
    }
    return element
}
// 调用这个函数
tag('div',{ className: 'row', textContent: 'Hi'})
```

**return 多个值**

```js

function myFunction(){
    let keys = 1
    let hash = 2
    return {
		'keys': keys,
		'hash': hash
	}
}
// 调用
let demo = myFunction()
demo.keys
demo.hash
```



## CSS属性

**将元素的文本内容字母变为大写**

```
text-transform: uppercase;
```

**背景图片布局**

```css
body {
    background: url(../img/rs-cover.jpg);
    /* 背景图片水平居中，垂直居中 */
    background-position: center center;
    /* 盖住我当前div的所有面积，按比例缩放。大概就是按照div的比例缩放的意思 */
    background-size: cover;
}
```



## 使用的工具

在线图片压缩：https://compressjpeg.com/zh/