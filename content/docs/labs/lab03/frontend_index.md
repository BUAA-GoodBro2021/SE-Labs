---
title: '前端实验指南'
weight: 2001
---

# Lab03 前端基础

## 实验目的

- 了解 Vue 框架的基本使用
- 熟悉 Vue CLI 的基础命令
- 掌握 Vue-Router、Vuex 与 Vue 的集成
- 掌握 ElementUI 的基础使用
- 掌握使用 Axios 发送网络请求的方法
- 熟悉 Vue 单页面组件的使用

## 资源链接

<a href="https://bhpan.buaa.edu.cn:443/link/3A508B02D5CE20902AE2983009CE5D1B" target="_blank">https://bhpan.buaa.edu.cn:443/link/3A508B02D5CE20902AE2983009CE5D1B</a>

Valid Until: 2023-07-15 23:59

## 实验指南
 
1. 查看资源链接中 **Vue** 和 **CSS** 相关的内容
2. 完成实验作业并于 3.31 日晚 12 点前提交至 <a href="https://scs.buaa.edu.cn/" target="_blank">软院云平台</a>

## 实验作业

根据 `作业.pdf` 中的作业要求完成作业，并将 **文档** 和 **演示视频** 打包提交到云平台上。

### 任务 1

使用 Vue CLI 创建一个自己的 Vue 项目，项目至少包含 Vue-Router 和 Vuex，其他依赖项可以自行决定要不要添加。

### 任务 2

在 views 中新建一个单页面组件，将其命名为 `Login.vue`。注册路径为 `/login` 的路由(修改 `router/index.js` )，并将 `Login.vue` 挂载到该路由下。在首页加入该页面的入口(如下图所示)。

![状态图1](/SE-Labs/images/lab3/状态图1.png)

<span style="color: red">router/index.js 的代码截图</span>

### 任务 3

在 `store/index.js` 中注册名为 `isLogin` 的状态(初始为 false 即未登录)，用于判断用户是否登录。对该状态增加两个 mutation，名为 login 和 logout，分别用于登录和登出。

<span style="color: red">store/index.js 的代码截图</span>

### 任务 4

在 Home 页面使用条件渲染，如果登录则显示下面状态 1，否则显示状态 2。在状态 2 时，点击上下的 login 都应该可以跳转。

{{< tabs "vue-home" >}}
{{< tab "状态1" >}} ![状态图1](/SE-Labs/images/lab3/状态图1.png) {{< /tab >}}
{{< tab "状态2" >}} ![状态图2](/SE-Labs/images/lab3/状态图2.png) {{< /tab >}}
{{< /tabs >}}

<span style="color: red">Home 组件的代码截图</span>

### 任务 5

Login 组件中的按钮应该使用 ElementUI 的按钮，在未登录时显示状态 1，在登录时显示状态 2。

{{< hint info >}}
登录按钮和未登录按钮展示需要使用 v-if 条件渲染，两者各绑定一个事件，分别对应触发 vuex 的 mutation（login 和 logout）。
{{< /hint >}}

{{< tabs "vue-login" >}}
{{< tab "状态1" >}} ![状态图1](/SE-Labs/images/lab3/状态图3.png) {{< /tab >}}
{{< tab "状态2" >}} ![状态图2](/SE-Labs/images/lab3/状态图4.png) {{< /tab >}}
{{< /tabs >}}

<span style="color: red">Login 组件的代码截图</span>

## 实验报告

按照要求完成实验文档和演示视频，可以简要阐明你的思路

## 提交方式

- 截止时间：**2022/3/31 晚 12 点**

- 提交方式：[软院云平台](https://scs.buaa.edu.cn/)

- 提交内容：打包后的实验文档和演示视频，将其命名为：

  ```txt
  学号_姓名_第3次实验.zip
  ```
