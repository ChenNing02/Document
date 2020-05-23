---
title: Vuex 使用
---

## 安装
官方文档：[Vuex 安装](https://vuex.vuejs.org/zh/installation.html)

### 直接下载

https://unpkg.com/vuex

### 引用

[Unpkg.com](https://unpkg.com/) 提供了基于 NPM 的 CDN 链接。以上的链接会一直指向 NPM 上发布的最新版本。您也可以通过  `https://unpkg.com/vuex@2.0.0`  这样的方式指定特定的版本。

使用 Unpkg 引入最新版，( Vuex引入后会自动初始化 )：

 ```sh
<script src="https://unpkg.com/vue"></script>
<script src="https://unpkg.com/vuex"></script>
 ```

### NPM

```bash
npm install vuex --save
```

## 使用

官方文档：[Vuex 使用](https://vuex.vuejs.org/zh/guide/)

### 最简单的 Store

> **提示：** 我们将在后续的文档示例代码中使用 ES2015 语法。如果你还没能掌握 ES2015，[你得抓紧了](https://babeljs.io/docs/learn-es2015/)！

[安装](https://vuex.vuejs.org/zh/installation.html) Vuex 之后，让我们来创建一个 store。创建过程直截了当——仅需要提供一个初始 state 对象和一些 mutation：

```js
const store = new Vuex.Store({
state: {
  count: 10
},
mutations: {
  increment (state) {
    state.count++
  }
}
})
store.commit('increment') /* 提交 count 的值就会加一 */
console.log(store.state.count)  /* 打出11 */
```

### State

作用：主要用来获取数据

**代码**

html

```html
<div id="app"></div>
```

JavaScript

```js
const store = new Vuex.Store({
    state: {
        count: 10,
        myName: '小明',
        myEmail: '123456@qq.com'
    },
    mutations: {
        increment(state) {
            state.count++
        }
    }
})
const Counter = {
    template: `
    <div>
        <div>编号：{{ count }}</div>
        <div>姓名：{{ myName }}</div>
        <div>邮箱：{{ myEmail }}</div>
        <button @click="add()">编号+1</button>
    </div>
    `,
    computed: {
        count() {
            return this.$store.state.count
        },
		myName() {
            return this.$store.state.myName
        },
		myEmail() {
            return this.$store.state.myEmail
        },
    },
    methods: {
        add() { this.$store.commit('increment') }
    }
}
const app = new Vue({
    el: '#app',
    store,
    components: { Counter },
    template: `
    <div>
        <counter></counter>
    </div>
    `
})
```

> 代码预览链接：https://jsbin.com/dunarom/edit?html,js,output 

其中 Counter 对象的 computed 属性中的内容写成如下形式简写：

```js
computed: {
	...Vuex.mapState(['count', 'myName', 'myEmail'])
}
```

> 代码预览链接：https://jsbin.com/dunarom/1/edit?html,js,output 

### Getter

作用：主要用来同步数据

在 `new Vuex.Store({})` 的参数中添加如下内容：

```js
const store = new Vuex.Store({
    state: {
        count: 10,
        myName: '小明',
        myEmail: '123456@qq.com'
    },
    mutations: {
        increment(state) {
            state.count++
        },
        modifyName(state, newName){
            state.myName = newName
        }
    },
    getters: {
        myData(state){
            return '编号为 '+state.count+ ' 的 ' +state.myName + ' 的邮箱是 ' + state.myEmail
        }
    }
})
```

在 Counter 对象中的 computed 属性中添加如下内容

```js
computed: {
    myData(){
    	return this.$store.getters.myData
    },
    ...Vuex.mapState(['count', 'myName', 'myEmail'])
}
```

上面的代码可以写成以下格式

```js
computed: {
    ...Vuex.mapState(['count', 'myName', 'myEmail']),
    ...Vuex.mapGetters(['myData'])
}
```

在控制台 commit 数据，小明就会改为小红，如下

```js
store.commit('modifyName', '小红')
```

最终代码

代码，预览链接

### Mutation

作用：主要用来修改数据

Mutation 的代码在 store 中就用到了

```js
mutations: {
    increment(state) {
        state.count++
    }
}
```

