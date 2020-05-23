---
title: "Vue-cli 使用"
---

Vue 命令行入门项目之 - 井字棋

## 创建

首先打开命令行工具，安装 Vue

可以使用下列任一命令安装这个新的包 ( 推荐使用 yarn 安装 )：

```bash
npm install -g @vue/cli
# 或
yarn global add @vue/cli 
```

更新 yarn 的 vue-cli 

```bash
yarn global add @vue/cli
```



安装后，可以用这个命令来检查其版本是否正确：

```bash
vue --version
```

创建一个当前项目的目录，进入这个目录

运行以下命令来创建一个新项目：

```bash
vue create .  # 表示在当前目录下创建 
vue create hello-world # 表示创建在一个指定目录下
```

运行后会出现以下问题

```bash
Vue CLI v4.0.4
# 是否要在当前目录创建这个项目，输入 y/n 选择，此次选择默认Y
? Generate project in current directory? (Y/n)
# 选择使用的默认配置，此处选择第二个，方向键上下切换，回车选择
? Please pick a preset: (Use arrow keys)
> default (babel, eslint)
  Manually select features
# 自定义选择所需要的功能，空格选中/取消，方向键切换，回车确认,此次只选中 Babel 即可
? Check the features needed for your project: (Press <space> to select, <a> to toggle all, <i> to invert selection)
>(*) Babel
 ( ) TypeScript
 ( ) Progressive Web App (PWA) Support
 ( ) Router
 ( ) Vuex
 ( ) CSS Pre-processors
 (*) Linter / Formatter
 ( ) Unit Testing
 ( ) E2E Testing
# 选择配置分开存放或所有配置都存放在 package.json 中，此次选择默认即可，回车确认
? Where do you prefer placing config for Babel, PostCSS, ESLint, etc.? (Use arrow keys)
> In dedicated config files
  In package.json
# 需要将当前项目备份，为以后项目使用吗，此次选择 N 
? Save this as a preset for future projects? (y/N)
# 选择默认打包工具，如果没有此选项说明你只安装了一个打包工具
? Pick the package manager to use when installing dependencies: (Use arrow keys)
> Use Yarn
  Use NPM
```

简写：

`v-on:click`

```html
v-on:click="onClickSelf" 
可以简写为：
@click="onClickSelf" 
```

`v-bind:`

```html
v-bind:title="提示信息"
可以简写为：
:title="提示信息"
```

​	组件点击事件

App.vue

```vue
<Cell v-on:click="console.log(1)" />
```

Cell.vue

```vue
<!-- 当前组件被点击时, 在组件的事件中调用this.$emit('click') -->
<template v-else>
	<div class="circle" v-on:click="onClickSelf"></div>
</template>
<script>
export default {
  methods: {
    onClickSelf() {
      this.$emit("click");
    }
  }
};
</script>
```

## 部署

打包之前需要在项目根目录创建 ` vue.config.js ` 并且含以下内容

```js
module.exports = {
  publicPath: process.env.NODE_ENV === 'production'
    ? '/my-project/'  // 生产环境目录
    : '/'  // 开发环境目录
}
```

> 其中 my-project 就是你当前项目 dist 目录加 dist 目录上级目录总路径

然后将文件打包到 dist 目录

```
yarn build
```

具体参阅 Vue-cli 文档：[部署 - Github Pages](https://cli.vuejs.org/zh/guide/deployment.html#github-pages)

## 使用到的API

### Math.floor()

 **`Math.floor()`** 返回小于或等于一个给定数字的最大整数。 

>  Note:  **`Math.floor() === `**向下取整 

就是取当前数的最小整数，例如：

```javascript
console.log(Math.floor(0.2))  // 打出 0
console.log(Math.floor(1.5))  // 打出 1
console.log(Math.floor(2.8))  // 打出 2
```

查看 MDN

[MDN 文档 - `Math.floor()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Math/floor) 