---
title: "Vue 入门案例"
date: 2019-09-01 18:29:26
---

几个 Vue 入门的小案例

在使用 Vue 前注意引入一个 Vue 库，当前案例使用的是 script 标签引入如下版本

```html
<script src="https://cdn.bootcss.com/vue/2.6.10/vue.js"></script>
```

## 按钮开/关提示
**代码**
{{< tabs "tabs-01" >}}
{{< tab "html" >}}

```html
<div id="app">
    <button v-on:click="go">开/关</button>
    <p v-if="open">我是文字内容</p>
</div>
```
 {{< /tab >}}
{{< tab "JavaScript" >}} 
```javascript
let app = new Vue({
    el: '#app',
    data: { open: false },
    methods: {
        go(){ this.open = !this.open }
    }
})
```
{{< /tab >}}
{{< tab "CSS" >}}
```css
p { 
    border: 1px solid #ccc; 
    padding: 10px; 
    width: 200px;
}
```
{{< /tab >}}
{{< /tabs >}}

## 鼠标悬浮提示

**代码**

{{< tabs "鼠标悬浮提示" >}}
{{< tab "html" >}}
```html
<div id="app">
    <p v-bind:title="xxx">鼠标悬浮当前文字显示提示</p>
</div>
```
{{< /tab >}}
{{< tab "JavaScript" >}}

```javascript
let app = new Vue({
    el: '#app',
    data: { xxx: '我是文字提示' }
})
```
{{< /tab >}}
{{< tab "CSS" >}}

```css
p { 
    border: 1px solid #ccc; 
    padding: 10px; 
    width: 200px;
}
```
{{< /tab >}}
{{< /tabs >}}

## 简单的轮播
**代码**
{{< tabs "简单的轮播" >}}
{{< tab "html" >}} 
```html
<div id="app">
    <div>
        <div class="window">
            <div class="demo" v-bind:style="{transform: transformValue}"></div>
        </div>
        <button v-on:click="go(0)">1</button>
        <button v-on:click="go(1)">2</button>
        <button v-on:click="go(2)">3</button>
    </div>
</div>
```
{{< /tab >}}
{{< tab "JavaScript" >}} 
```javascript
let app = new Vue({
    el: '#app',
    data: { transformValue: '' },
​    methods:{
​        go(index){ this.transformValue = `translateX(${-100*index}px)` }
​    }
})
```
{{< /tab >}}
{{< tab "CSS" >}} 
```css
body { padding: 100px 0 0 200px; }
.window { width: 100px; height: 100px; border: 1px solid blue; }
.demo { 
	width: 300px; 
	height: 100px; 
	background: rgba(0, 0, 255, 0.3); 
    transition: all 0.3s; 
}
```
{{< /tab >}}
{{< /tabs >}}

## tab 切换

**简单的切换**

{{< tabs "tab 切换" >}}

{{< tab "html" >}}
```html
<div id="app">
    <div>
        <ol>
            <li v-on:click="selected = 0">1</li>
            <li v-on:click="selected = 1">2</li>
            <li v-on:click="selected = 2">3</li>
        </ol>
        <ol>
            <li v-show="selected === 0">内容1</li>
            <li v-show="selected === 1">内容2</li>
            <li v-show="selected === 2">内容3</li>
        </ol>
    </div>
</div>
```
{{< /tab >}}
{{< tab "JavaScript" >}} 
```javascript
let app = new Vue({
    el: '#app',
    data: { selected: 0 }
})
```
{{< /tab >}}
{{< tab "CSS" >}}
```css
li { 
	list-style: none; 
	display: inline-block; 
	padding: 10px; 
    border: 1px solid #ccc;
}
```
{{< /tab >}}
{{< /tabs >}}

**for循环切换**

{{< tabs "for循环切换" >}}
{{< tab "html" >}}
```html
<div id="app">
    <div>
        <ol>
            <li v-for="tab in tabs"
                v-on:click="selected = tab.name"
                v-bind:class="{active: tab.name === selected}"
            >{{ tab.name }}</li>
        </ol>
        <ol>
            <li v-for="tab in tabs"
                v-show="selected === tab.name"
            >{{ tab.content }}</li>
        </ol>
    </div>
</div>
```
{{< /tab >}}
{{< tab "JavaScript" >}}
```javascript
let view = new Vue({
    el: '#app',
    data: {
        selected: 'a',
        tabs: [
            { name: 'a', content: '内容a' },
            { name: 'b', content: '内容b' },
            { name: 'c', content: '内容c' }
        ]
    }
})
```
{{< /tab >}}
{{< tab "CSS" >}}
```css
ol, li { margin: 0; padding: 0; }
li { 
    list-style: none; 
    display: inline-block; 
    cursor: pointer;
    padding: 10px; 
    margin: 4px; 
    border: 1px solid blue; 
}
.active { background-color: #ccc; }
```
{{< /tab >}}
{{< /tabs >}}
