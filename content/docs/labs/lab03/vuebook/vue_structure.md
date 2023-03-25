---
title: 'Vue 项目架构'
weight: 20033
---

# Vue 项目架构

在上一页我们创建了一个初始的 vue2/vue3 项目，现在本文将对这个几乎空白的项目框架进行简要介绍。

{{< hint info >}}
阅读本文时并不要求理解 Vue 项目中各部分是如何编写的，只大致了解它们的用途
{{< /hint >}}

## 总体概述

下面是我们创建的项目的文件目录：

![vue-structure](/SE-Labs/images/lab3/vue-structure.png)

简要介绍如下：

| 目录/文件    | 说明                                                         |
| ------------ | ------------------------------------------------------------ |
| node_modules | npm 加载的项目依赖模块                                       |
| public       | 静态资源，build 构建后为根目录，含网站导航栏图标、首页入口文件 |
| src          | 开发做的事情基本都在这个目录下，含：<br>assets: 放置一些图片、字体等资源<br/>components: 放置组件文件，一般为全局组件<br/>router: 网站路由跳转设置<br/>store: 前端数据存储<br/>views: 放置各页面文件<br/>App.vue: 项目入口文件<br/>main.js: 项目的核心文件，在这里可以导入各种全局依赖 |
| .xxx文件     | 配置文件，包括语法配置、git配置(.gitignore)等                |
| package.json | 项目 npm 包配置文件                                          |
| package-lock.json | 项目 npm 包版本控制文件                                 |
| README.md    | 项目的说明文档                                               |

下面对主要模块进行讲解

## node_modules

node_modules 目录下放置项目所需要的依赖环境，当使用 `npm install packageName --save` 命令给项目添加依赖时，信息会记录于 `package.json` 文件的 dependencies 中，而依赖的包将存储于 node_modules。

在该目录下，可以发现有我们在创建项目时选择的 vue-router 包，这是用于管理路由跳转的依赖。之后如果引入了某个 npm 包后，由于文档缺失等原因不熟悉其中的某个 API，可以进入对应的文件夹查看源码。

在编辑器中可以看到该目录名字显示灰色的，因为它在 .gitignore 是被忽略的。在合作开发项目中，往往使用 git 来协调配合，而该目录内容庞大，且并非由程序员编写，因此往往不加入 git 中，在新机器上使用 npm install，则会根据 package.json 的配置信息生成 node_modules。


## public

初始项目中，public 目录下有 favicon.ico 和 index.html 两个文件，前者是网站图标 logo，注意如果说我们自己的项目也希望使用个性化的网站图标，那么必须是 ico 格式的；后者是网站首页入口文件，代码如下：

```html
<!DOCTYPE html>
<html lang="">
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width,initial-scale=1.0">
    <link rel="icon" href="<%= BASE_URL %>favicon.ico">
    <title><%= htmlWebpackPlugin.options.title %></title>
  </head>
  <body>
    <noscript>
      <strong>We're sorry but <%= htmlWebpackPlugin.options.title %> doesn't work properly without JavaScript enabled. Please enable it to continue.</strong>
    </noscript>
    <div id="app"></div>
    <!-- built files will be auto injected -->
  </body>
</html>
```

上述代码包含了一个网页最基本的信息，在 head 标签中，我们可以编写网站的标题 title、编码 charset、图标 icon、描述 description、关键词 keywords 等信息；在 body 标签中，vue 项目通常只需要包含 `<div id="app"></div>`，表示 App.vue 文件。

## src

### assets

assets 目录放置项目所需要的资源，如图片、字体等，并由 vue 文件使用。

### components

components 目录放置项目的全局组件。

在项目开发中，存在部分小模块需要多次复用，比如导航栏、某些样式的按钮等，通常被提取出来作为全局组件。与之对应的是局部组件，通常是某个页面内容较多，使用多个 vue 文件编写，其中某个 vue 文件和其它文件为父子关系，父引入子，实现低耦合的特性。

初始项目中，该目录下有 `HelloWorld.vue` 文件，可以看到在 `views/HomeView.vue` 中，引入了该文件。


> 在这里也简略说明一下 vue 文件的组成。vue 文件主要由三部分组成：
> * template：html，网页结构内容
> * script：该 vue 文件所需的数据对象格式、js 方法等
> * style：css 页面样式

### router

`router/index.js` 编写路由规则，即赋予 vue 文件相应的相对路由，核心代码为：

```js
const routes = [
  {
    path: '/',
    name: 'Home',
    component: Home
  },
  {
    path: '/about',
    name: 'About',
    component: () => import('../views/AboutView.vue')
  }
]
```

其中，path 为分配的相对路由，component 指定 vue 视图页面。

初始项目运行在 `localhost:8080` 时，访问 `localhost:8080/about` 将显示 `About.vue` 的内容。

### store

store 目录下主要放置前端存储数据的格式，利用 vuex 和 localStorage 在用户的网页端保存基本的用户信息。例如用户登录之后，将用户名存于前端，这样在渲染网页时可以直接使用，且向后端发送请求时可以携带用户名，以验证用户的登录信息是否有效。

vuex 所代表的思路是实现组件间通信的最终解决方案，它功能强大，原理严谨，同学们在学习过程中只要学会了它，可以不去学习 **事件总线**，**消息订阅和发布** 也可以只做了解。[点击这里查看 vuex 中文文档](https://vuex.vuejs.org/zh/guide/)

vuex 的持久化存储也是 vuex 中必须学习的一环。所谓持久化存储就是指借助浏览器保存前端记录的信息，这样就不会在关闭浏览器时就丢失所有信息。

在 vue3 中，为了进一步简化 vuex 的步骤，pinia 逐渐崛起，甚至在 Vue 官方最新发布的 create-vue （新一代 vue + vite 项目创建工具）中，pinia 已经代替 vuex 成为官方推荐设置的 状态管理工具。[点击这里查看 pinia 中文文档](https://pinia.web3doc.top/)

![pinia](/SE-Labs/images/lab3/pinia.png)


### views

components 和 views 文件夹下均放置的是 vue 文件，不同的是，前者是可以被多个“页面”复用的“页面碎片”，后者是作为项目中的一整个“页面”，往往对应了一个路由。

看初始项目，里面有 `About.vue` 和 `Home.vue`，分别对应路由 `/about` 和 `/`。简单看一下这两个文件：

`About.vue`：内容很简单，仅包含 template 部分，仅仅是一句话。
```html
<template>
  <div class="about">
    <h1>This is an about page</h1>
  </div>
</template>
```
`Home.vue`：包含 html 和 script 两部分，可以看到在 script 标签中引入了 `HelloWorld` 组件，然后在 html 部分中进行调用，这样该页面的效果为，`logo` 图片加 `HelloWorld` 组件。

```html
<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'HomeView',
  components: {
    HelloWorld
  }
}
</script>
```

这里对 `@` 进行一个简要说明：所谓 `@` 可以从英文注释中看出，它是一个 `/src` 的别名。我们通常叫它软链接。可以想象，当 `src` 下目录结构复杂时，如果使用相对地址进行寻址，那么地址中的 `../` 会有很多，采用 `@` 就可以以 `/src` 为基地址简化路径书写。这里的配置在 `jsconfig.json` 中可以看到：

```json
// jsconfig.json
{
  "compilerOptions": {
    "target": "es5",
    "module": "esnext",
    "baseUrl": "./",
    "moduleResolution": "node",
    "paths": {
      "@/*": [
        "src/*"
      ]
    },
    "lib": [
      "esnext",
      "dom",
      "dom.iterable",
      "scripthost"
    ]
  }
}
```


### App.vue

无论是 vue2 还是 vue3，App.vue 都是整个项目的入口文件，该文件描述整个网站将渲染的内容。一般来说，我们会把整个项目都会使用的样式在这里配置。一个好的项目应该避免在 `App.vue` 中有过于繁琐的内容。具体的实现细节应该尽量抽离为 views 文件夹下的 vue 文件，在  `App.vue` 中仅有对于某些子组件的引用，或者是路由的切换。

```html
<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <router-view/>
  </div>
</template>
```

如上述代码，它由 `nav` 的代码块和 `router-view` 组成。前者是两个超链接，有点类似于网站的导航栏，在各个路由下都会展示；后者表示根据路由渲染对应的 vue 组件，如果当前是 `/about` 则渲染 `About.vue` 文件描述的内容。

### main.js

main.js 是项目的核心文件，在这里可以导入各种全局依赖。比如全局导入 [elementUI](https://element.eleme.cn/#/zh-CN)（Vue3 对应的是 [elementPlus](https://element-plus.org/zh-CN/#/zh-CN)） 等 UI 组件库或 [ECharts](https://echarts.apache.org/zh/index.html) 可视化图表库等，`npm install` 后将在该文件中全局引入。

#### Vue2 版本

```js
import Vue from 'vue'
import App from './App.vue'
import router from './router'
import store from './store'

Vue.config.productionTip = false

new Vue({
  router,
  store,
  render: h => h(App)
}).$mount('#app')
```

上面是 Vue2 项目中的 main.js，简单分析后可以看出，它引入了 Vue 核心运行库中的 `Vue` 构造函数、`App.vue`、vue-router 相关文件创造的 router 对象，vuex 创建的 store 对象。

在将工具库导入后，利用 Vue 创建一个 Vue 实例对象，并在这个过程中将 App 组件渲染到 `index.html` 中 `id="app"` 的 DOM 节点上（即 `<div id="app"></div>`）。


#### Vue3 版本

```js
import { createApp } from 'vue'
import App from './App.vue'

import router from './router'
import store from './store'

createApp(App)
.use(router)
.use(store)
.mount('#app')
```

上面是 Vue3 项目中的 `main.js`，可以看到，引入的不再是 `Vue` 构造函数了，而是一个名为 `createApp` 的工厂函数；利用这个工厂函数，创建应用实例对象，将引入的 router 和 store “使用”后，再挂载到 `index.html` 中 `id="app"` 的 DOM 节点上（即 `<div id="app"></div>`）。

## Bonus

事实上，在真正的项目中，还有一些文件目录是不可或缺的。

![vue-structure2](/SE-Labs/images/lab3/vue-structure2.png)

### api

这个文件夹往往用于放置前端向后端发起请求的函数。但是，作为其模板的 `request.js` 和配置 **请求拦截器** 和 **响应拦截器** 的 `intercept.js` 往往是放在 `utils` 文件夹下的。

关于前后端如何进行请求交互，这里推荐大家了解 Promise 的基础知识，并阅读 [Axios 中文文档](https://www.axios-http.cn/)。

### constants

顾名思义，这里就是用于放置在各个文件中规定好的通用常量。比如说一些约定的键值。就类似于操作系统课程中，对于一些地址、指令、权限的宏定义。

### utils

这个文件夹主要放置一些工具类，最常见的有两类：字符串处理函数 和 文件处理函数。

字符串处理函数是指一些通用的处理逻辑，比如说前端在拿到后端数据库的时间戳后需要进行格式化处理。

{{< hint info >}}
关于时间相关的字符串处理，这里强烈推荐一个工具库 [moment.js](https://momentjs.com/docs/#/use-it/)
{{< /hint >}}

文件处理函数则是指对一些特定格式文件的操作，比如说对于 Excel/CSV 表格文件的解析，对于 Word/PDF 文件的导出等。此外文件的上传的一些高级操作（比如秒传）也可以放在这里。


# 结语

vue 虽然号称是当前入门最简单的主流前端框架，但是相比三件套本身，需要新掌握的东西可以说成指数级增长。我们思量再三，最终决定不在指导书中对于 vue 的语法进行介绍——因为网上已经有太多好的教程，我们这里的一番絮语也无法让大家快速、扎实地入门 vue。比表达，几页指导书很难比得过翔实的视频教程，比内容，我们的一家之言又很难比得上官方的说明文档。因此，我们这里能做的，仅仅是作为一个前辈，将一些别的地方提及甚少的细节、学习路上质量极高的资料收集汇总给大家。

前端之路漫漫，诸君仍需努力。