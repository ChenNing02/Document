---
title: "属性修饰符"
date: 2020-05-25T09:49:29+08:00
slug: 1b4dd519
draft: false
weight: 80
---

MDN 文档：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperty

## 变量访问与修改

```js
var i = 2
var newObject = {
    get x(){ return i },
    set x(value){
        i = value + i
        return i
    }
}
newObject.x // 2
newObject.x = 2
newObject.x // 4
```

## 追加访问修改函数

假如一个对象之前并没有 get set 方法，在ES6的语法中可以使用以下方式追加

```js
let i = 2
let o = {
    a: 1,
    b: 2
}
Object.defineProperty(o, 'x', {
    get(){ return i },
    set(value){
        i = value + i
        return i
    }
})
o.x = 100
o.x // 102
```

## undefined 的实现原理

在JS中，undefined 不是关键字 而是一个只读的变量，如下：

```js
var function // 报错
var null // 报错
var this // 报错
var undefined // undefined
undefined = 1
undefined // undefined
```

如果给变量添加 get 函数，它就可以成为一个只读的函数：

```js
let o = {
    get name(){return 'sun'}
}
o.name // "sun"
o.name = 'jack'
o.name // "sun"
```

或者给变量设置 writable 属性为 false

```js
let o = {name: undefined}
Object.defineProperty(o, 'name', {writable: false})
o.name // undefined
o.name = 'jack'
o.name // undefined
```

也可以将 writable 属性设置为 true 将只读属性变回可写的

```js
let o = {name: undefined}
Object.defineProperty(o, 'name', {writable: true})
o.name = 'xxx'
o.name // "xxx"
```

## configurable 禁止修改属性

禁止修改属性，如：value，writable，get，set等

当且仅当该属性的 configurable 键值为 true 时，该属性的描述符才能够被改变，同时该属性也能从对应的对象上被删除。
默认值为 false。（设置 configurable 为 true 时，无法修改属性）

将上面的对象 o 的 configurable 设置为 true

```js
let o = {name: undefined}
Object.defineProperty(o, 'name', {writable: false, configurable: false})
// 此时再修改writable的属性会报错：
Object.defineProperty(o, 'name', {writable: true}) // 报错
```

## enumerable 可枚举属性

默认情况下 遍历某个对象或数组，并不能完全遍历该对象/数组的所有属性

```js
// 对象的toString属性并不能被遍历
let obj = {a: 1, b: 2, c: 3}
for(let key in obj){
    console.log(key)
}
// a b c

// 数组的length属性并不能被遍历
let num = [1, 2, 3]
for(let key in num){
    console.log(key)
}
// 0 1 2
```

我们可以通过给对象添加一个 enumerable 修饰符来修改，该对象的属性是否可遍历

```js
let obj = {a: 1, b: 2, c: 3}
Object.defineProperty(obj, 'b', {value: 2, enumerable: false})
for(let key in obj){
    console.log(key)
}
// a c
```

查看对象的属性描述

```js
Object.getOwnPropertyDescriptor(obj, 'b')
// {value: 2, writable: true, enumerable: false, configurable: true}
Object.getOwnPropertyDescriptor(obj, 'a')
// {value: 1, writable: true, enumerable: true, configurable: true}
```

可以批量的给属性添加修饰符

```js
Object.defineProperties(o, {
    a: {value: 1, writable: false},
    b: {value: 2, writable: true}
})
o.a = 2
o.a // 1
o.b = 4
o.b // 4
```

## 使用Symbol设置对象的key

```js
let s = Symbol()
let o = {[s]: 1}
o[s] // 1
```

Symbol 设置的key只能通过 `getOwnPropertySymbols` 的方式获取

```js
// 获取对象的key 方法1
Object.keys(o) // []
// 获取对象中的 Symbol key
Object.getOwnPropertySymbols(o) // [Symbol()]
// 获取对象的key 方法2
Object.getOwnPropertyNames(o) // []
```

## 使用 parcel 兼容IE

官方文档：https://parceljs.org/getting_started.html