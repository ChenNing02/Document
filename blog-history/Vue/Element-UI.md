---
title: Element UI
date: 2019-09-01 18:29:26
---

## 分页组件

### 常用属性

| 名称         | 作用                                 | 类型    | 可选值 | 默认值 |
| ------------ | ------------------------------------ | ------- | ------ | ------ |
| small        | 使用小型分页样式                     | boolean |        | false  |
| background   | 为分页按钮添加背景色                 | boolean |        | false  |
| page-size    | 每页显示数据个数 (支持 .sync 修饰符) | number  |        | 10     |
| total        | 数据总个数 (总条目数)                | number  |        |        |
| current-page | 当前页数 (支持 .sync 修饰符)         |         |        | 1      |

### 事件

| 名称           | 说明                              | 回调参数 |
| -------------- | --------------------------------- | -------- |
| current-change | 当前页 (currentPage) 改变时会触发 | 当前页   |

常用带跳转案例

```vue
<el-pagination
  background
  @current-change="handleCurrentChange"
  :current-page.sync="currentPage1"
  :page-size="100"
  layout="total, prev, pager, next"
  :total="1000">
</el-pagination>
```

