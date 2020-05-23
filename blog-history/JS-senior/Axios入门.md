---
title: "Axios 入门"
---

## 安装

### npm 安装

```bash
npm install axios
```

### yran 安装

```bash
yarn add axios
```

### CDN 引入

```html
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
```

>官方文档：[GitHub-axios](https://github.com/axios/axios#installing)

## 使用

**get请求**

```javascript
axios.get('/user?ID=12345').then((response)=>{
    console.log(response)
}).catch((error)=>{
    console.log(error)
})
```

## 拦截器

案例

在返回 response 之前执行 `.use()` 中的函数

```javascript
axios.interceptors.response.use(function(response){
  response.data = {
    'name': 'frank'
  }
  return response
})

axios.get('/books/1').then((response)=>{
  console.log(response)
})
```

**根据请求路由判断**

当请求为 get 请求并且请求的 url 是 `'/books/1'` 才会返回数据 data 的值

```javascript
axios.interceptors.response.use(function(response){
  let config = response.config
  let {method, url, data} = config
  if(url === '/books/1' && method === 'get'){
    response.data = {
      'name': 'frank'
    }
  }
  return response
})

axios.get('/books/1').then((response)=>{
  console.log(response)
})
```

### 虚拟服务器

模拟服务器返回数据

