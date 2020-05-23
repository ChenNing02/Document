---
title: ES 6 新特性列表
---

# ES 6 新特性列表

由 [饥人谷](http://jirengu.com/) 搜集整理。点击链接，查看中文学习资料。

- 作用域
  - [块级作用域](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/block)
  - [块级变量 let](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/let)
  - [块级常量 const](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/const)
- 箭头函数
  - `sum = (a, b) => a + b`
  - `nums.forEach( v => { console.log(v) })`
  - 词法 this
- 参数处理
  - [默认参数值](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions/Default_parameters)
  - [剩余参数](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions/Rest_parameters)
  - [展开运算符](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Spread_operator)
- 模板字面量
  - [多行字符串](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/template_strings#多行字符串)
  - [字符串插值](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/template_strings#表达式插补)
  - [带标签的模板字面量](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/template_strings#带标签的模板字符串)
  - [原始字符串](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/template_strings#原始字符串)
- 原有字面量加强
  - 更安全的二进制字面量（0b1111101）
  - 更安全的八进制字面量（0o767）
  - 字符串支持 Unicode
    - [String.fromCodePoint](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/fromCodePoint)
    - [String.prototype.codePointAt](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/codePointAt)
  - 正则表达式字面量添加 [Unicode 支持（u 标记）](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/RegExp/unicode)
  - 正则表达式添加 y 标记，支持[粘滞匹配](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/RegExp#Example:_Using_a_regular_expression_with_the_sticky_flag)
- 对象属性加强
  - 属性定义支持短语法 `obj = { x, y }`
  - 属性名支持表达式 `obj = {["baz" + quux() ]: 42}`
  - 添加 [`__proto__` 属性](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/proto)，但不建议使用
- 解构赋值
  - 数组匹配 `[ b, a ] = [ a, b ]`
  - 对象匹配 `let { a, b, c } = objABC`
  - 参数匹配 `function g ({ name: n, val: v }) {}`
- 模块
  - [导入（import）](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/import)
  - [导出（export）](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/export)
  - [默认导出（export default）](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/export#默认导出)
- 类
  - [使用 extends 实现继承](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Classes#使用_extends_创建子类)
  - [重写构造器](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Classes#Species)
  - [super 关键字](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Classes#使用_super_引用父类)
- 迭代
  - [迭代器](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Iterators_and_Generators#迭代器)
  - [for of](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/for...of)
- [生成器](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Iterators_and_Generators#生成器（Generators）_一个更好的方法来构建遍历器)
- [Promise](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise)
- 元编程
  - [代理（Proxy）](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Proxy)
  - [反射（Reflect）](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Reflect)
- 新增数据类型
  - [Symbol 类型](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Symbol)
  - [Set 类型](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Set)
  - [Map 类型](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Map)
  - [WeakSet 类型](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/WeakSet)
  - [WeakMap 类型](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/WeakMap)
  - [TypedArray 类型](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/TypedArray)
- 原有内置对象 API 增强
  - [Object.assign](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/assign)
  - [Array.from](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/from)
  - [Array.of](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/of)
  - [Array.prototype.fill](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/fill)
  - [Array.prototype.find](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/find)
  - [Array.prototype.findIndex](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex)
  - [Array.prototype.copyWithin](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/copyWithin)
  - [Array.prototype.entries](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/entries)
  - [Array.prototype.keys](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/keys)
  - [Array.prototype.values](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/values)
  - [String.prototype.includes](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/includes)
  - [String.prototype.repeat](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/repeat)
  - [String.prototype.startsWith](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/startsWith)
  - [String.prototype.endsWith](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/endsWith)
  - [Number.EPSILON](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Number/EPSILON)
  - [Number.isInteger](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Number/isInteger)
  - [Number.isSafeInteger](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Number/isSafeInteger)
  - [Number.isFinite](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Number/isFinite)
  - [Number.isNaN(‘NaN’)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Number/isNaN) // false
  - [Math.acosh](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Math/反双曲余弦值)
  - [Math.hypot](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Math/hypot)
  - [Math.imul](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Math/imul)
  - [Math.sign](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Math/sign)
  - [Math.trunc](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Math/trunc)
- 尾递归优化

***

> 本文转载自：[饥人谷 - ES 6 新特性列表](https://fangyinghang.com/es-6-tutorials/)