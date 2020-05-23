---
title: JS 中的 Symbol 是什么？
---

# JS 中的 Symbol 是什么？

ES 6 引入了一个新的数据类型 Symbol，它是用来做什么的呢？

为了说明 Symbol 的作用，我们先来描述一个使用场景。

我们在做一个游戏程序，用户需要选择角色的种族。

```js
var race = {
  protoss: 'protoss', // 神族
  terran: 'terran', // 人族
  zerg: 'zerg' // 虫族
}

function createRole(type){
  if(type === race.protoss){创建神族角色}
  else if(type === race.terran){创建人族角色}
  else if(type === race.zerg){创建虫族角色}
}
```

那么用户选择种族后，就需要调用 createRole 来创建角色：

```js
// 传入字符串
createRole('zerg') 
// 或者传入变量
createRole(race.zerg)
```

一般传入字符串被认为是不好的做法，所以使用 createRole(race.zerg) 的更多。

如果使用 createRole(race.zerg)，那么聪明的读者会发现一个问题：race.protoss、race.terran、race.zerg 的值为多少并不重要。



改为如下写法，对 createRole(race.zerg) 毫无影响：

```js
var race = {
  protoss: 'askdjaslkfjas;lfkjas;flkj', // 神族
  terran: ';lkfalksjfl;askjfsfal;skfj', // 人族
  zerg: 'qwieqwoirqwoiruoiwqoisrqwroiu' // 虫族
}
```

也就是说：

**race.zerg 的值是多少无所谓，只要它的值跟 race.protoss 和 race.terran 的值不一样就行。**



Symbol 的用途就是如此：Symbol 可以创建一个独一无二的值（但并不是字符串）。

用 Symbol 来改写上面的 race：

```js
var race = {
  protoss: Symbol(),
  terran: Symbol(),
  zerg: Symbol()
}

race.protoss !== race.terran // true
race.protoss !== race.zerg // true
```

你也可以给每个 Symbol 起一个名字：

```js
var race = {
  protoss: Symbol('protoss'),
  terran: Symbol('terran'),
  zerg: Symbol('zerg')
}
```

不过这个名字跟 Symbol 的值并没有关系，你可以认为这个名字就是个注释。如下代码可以证明 Symbol 的名字与值无关：

```js
var a1 = Symbol('a')
var a2 = Symbol('a')
a1 !== a2 // true
```

如果你觉得我说得还是太复杂了，看不懂，你可以记一句话：

Symbol 生成一个全局唯一的值。

------

以上，就是 Symbol 的简述，更详细更权威的知识参考下面的自学链接。

自学链接：

MDN： [Symbol - JavaScript](https://link.zhihu.com/?target=https%3A//developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Symbol)

阮一峰：[ECMAScript 6入门](https://link.zhihu.com/?target=http%3A//es6.ruanyifeng.com/%23docs/symbol)

------

> 本文转自：https://zhuanlan.zhihu.com/p/22652486?refer=study-fe

