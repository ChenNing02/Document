---
title: "ES6的对象"
date: 2020-05-25T08:18:51+08:00
slug: b25cf121
draft: false
weight: 70
---

## 创建对象

### 之前的创建方法

```js
var a1 = new Object()
var a2 = {}
```

> 上面的两种方法创建的对象都有对象的原型链属性

### ES6新增方法

```js
let b1 = Object.create(null) // 没有对象的原型链
let b2 = Object.create(Object.prototype) // 传入对象的原型链
```

> ES6方法创建的对象，只有在传入 `Object.prototype` 是才会生成具有对象原型链的空对象
> 当传入的值为 null 时，生成的对象是不具有原型链的（也就是真正的空对象）

## 对象赋值

```js
let a = 1
let b = 2
let object = { a: a, b: b }
// 也可以简化为：let object = { a, b }
```

## 对象 key 传参

```js
let _name = 2
let object = { [_name]: 1 } // {2: 1}
// 对象中[]的key可以做复杂运算，如：
let object = { [_name*2+_name/3]: 1 } // {4.666666666666667: 1}
```

## 对象属性值访问与修改

当给一个对象定义 `get xxx()` 和 `set xxx()` 的方法时，访问这个对象的 `xxx` 属性将访问到 get 函数中返回的值。修改这个对象的 `xxx` 的值时，修改值将作为 set 的第一个参数传入，修改后的结果是 set 函数 return 的值

```js
let obj = {
    _age: 16,
    get age(){return obj._age},
    set age(value){return obj._age = value+1}
}
console.log(obj.age)// 16

obj.age = 100

console.log(obj.age) // 101
```

这样就可以给该 obj 的 age 属性做访问限制，如：

```js
let obj = {
    _age: 16,
    get age(){return obj._age},
    set age(value){
        if(value<100){
            return obj._age = value
        }else {
            return obj._age = 100
        }
    }
}

obj.age = 40
console.log(obj.age) // 40

obj.age = 1000
console.log(obj.age) // 100
```

### 使 `a == 1 && a == 2 && a == 3` 的值为 true

```js
let i = 0
// 给 window 添加一个属性，属性名是 a，a 有一个 get 函数
Object.defineProperty(window, 'a', {
    get(){
        i+=1
        return i
    }
})

a === 1 && a === 2 && a === 3 //true
```

> 原理，控制全局变量 a 的读取过程，每次访问 a 的值都会改变

## 对象浅拷贝

之前的写法

```js
let obj1 = {a: 1, b: 2, c: 3}
let obj2 = {}
for(let key in obj1){
    obj2[key] = obj1[key]
}
console.log(obj2) // {a: 1, b: 2, c: 3}
```

ES6写法1

```js
let obj1 = {a: 1, b: 2, c: 3}
let obj2 = Object.assign({}, obj1)
console.log(obj2) // {a: 1, b: 2, c: 3}
```

ES6写法2

```js
let obj1 = {a: 1, b: 2, c: 3}
let obj2 = {...obj1}
console.log(obj2) // {a: 1, b: 2, c: 3}
```

## 添加原型链

使用 `a = Object.create(b)` 的方法可以给对象添加新的原型链

```js
let a = {}
a.__proto__ === Object.prototype // true
let b = {
    sayHi(){
        console.log('hi')
    }
}
a = Object.create(b)
a.__proto__ === Object.prototype // false

a.__proto__ === b // true
```

访问对象原型链方法

```js
a.__proto__ // 第一种
Object.getPrototypeOf(a) // 第二种
```

查询对象的属性是否存在

```js
a.hasOwnProperty('__proto__') // 虽然__proto__是false，但是确实存在__proto__
```