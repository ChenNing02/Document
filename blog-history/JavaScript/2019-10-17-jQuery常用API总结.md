---
title: jQuery常用API总结
date: 2019-10-17 21:19:58
tags:
- jQuery
---

.CSS

获取指定CSS属性值

```js
$(element).css("background-color");
```

修改指定CSS属性值

```js
$(element).css("color","red")
```
修改多个属性值
```javascript
$(element).css({'background-color':'red','color':'blue'})
```

**jQuery 中两个不合理的 API** 

- `.hide()`
- `.show()`

当你给一个本来就 `display: none` 的元素添加 `.hide()` 然后再 `.show()` 的时候，会发现它的 display 变成了 block 

这说明 jQuery 无法真正还原你原本的 display 属性，它只是猜测你的 display 属性

**获取父元素的子元素**

```js
$(element).children()
```

**克隆当前元素**

```js
.clone(true) // 默认 false 添加 true 表示克隆当前元素所有内容，包含它的子元素，
```



**添加，删除 class 样式**

```js
$(element).addClass('active')
$(element).removeClass('active')
```

**动画执行完毕后执行事件**

```js
.one('transitionend', (e)=>{
	console.log('当前动画执行完毕')
})
```



**返回当前元素在父元素的第 n 个位置的索引**

```js
let index = $(element).index()
```

**获取存放元素的伪数组中索引为 index 的元素**

```js
$(elements).eq(index)
```

**给当前元素绑定执行指定事件**

```js
.trigger('click')
```

**获取当前兄弟元素中的所有除了当前元素以外 指定选择器 的元素**

```js
.siblings('.blue')
```

**鼠标进入元素事件**

```js
$(element).on('mouseenter', function(){ })       
```

**鼠标离开元素事件**

```js
$(element).on('mouseleave', function(){ })
```

