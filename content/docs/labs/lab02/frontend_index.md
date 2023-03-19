---
title: "前端实验指南"
weight: 2001
---

# Lab02 前端基础

## 实验目的

- 了解基础的 HTML，CSS，JS 语法
- 练习引入 css、js 代码
- 练习处理事件
- 练习修改页面样式
- 练习修改页面逻辑
- 练习使用浏览器控制台
- 回顾第 1 次实验课 git 的使用

## 资源链接

https://bhpan.buaa.edu.cn:443/link/3A508B02D5CE20902AE2983009CE5D1B

Valid Until: 2023-07-15 23:59

## 实验指南

1. 查看资源链接中的 **前端入门基础.mp4**、**前端入门基础.pdf**
2. 学习 JS 可以参考链接中的三本电子书，网页版可以参考 <a href="https://zh.javascript.info/" target="_blank">现代 JavaScript 教程</a>
3. 推荐使用 Chrome 浏览器进行开发，调试技巧可以参考 <a href="https://www.frontendwingman.com/Chrome/" target="_blank">Chrome DevTools 使用技巧 </a>
4. 在前端的学习和开发过程中，建议你时常参考 <a href="https://developer.mozilla.org/zh-CN/" target="_blank">✨✨MDN Web Docs✨✨</a>，这是前端开发的百科全书
5. 完成实验作业并于 3.25 日晚 12 点前提交至 <a href="https://scs.buaa.edu.cn/" target="_blank">软院云平台</a>

{{< hint info >}}
很多同学认为前端开发就是框架 + 组件库 + 搜索引擎。

熟悉框架语法并从组件库进行 CV 固然可以快速完成需求，但软工一作为一系列软件工程开发的开端，作为助教，我们还是希望同学们能在这几个月的学习过程中打好 JS 和 CSS 的基础，增加自己日后面对复杂需求时的底气，勿以浮沙筑高台。

个人建议在有必要时，可以在假期给自己的 JS 和 CSS 补补钙。这两者的内容都远比想象中要多得多。JS 中的正则和 Java 中有所区别，在表单应用和处理用户输入等地方，熟练正则能够节省很多功夫。可迭代对象的流函数也是批量操作数据的利器。CSS 就更不必多说了，浩如烟海的属性，无数 combo 的小配合和小技巧只有不断练习才能掌握。这里附上一个很有名的 **CSS 选择器** 练习链接：[“餐厅练习” CSS Dinner](https://flukeout.github.io/#)，动画 Q 萌，讲解翔实，非常推荐学完 CSS 选择器的同学检验自己的学习成果。
{{< /hint >}}

## 实验作业

你可以在所给资源的 homework 文件夹中找到实验文档并填写
{{< hint info >}}
本次实验建议使用 Live Server 拓展，我们可以在项目中将其作为一个服务器实时查看所开发的项目的效果。

安装拓展后，对 `index.html` 右键选择 `Open with Live Server` 开启服务。

![Live Server](/SE-Labs/images/lab2/LiveServer.png)

{{< /hint >}}

{{< hint info >}}
VSCode 中有很多好用的前端拓展，在这里进行简单推荐：

- Auto Close Tag : 自动闭合标签
- Auto Rename Tag : 自动重命名标签
- gitLens : 增强 git 版本控制
- open in browser : 在浏览器中打开当前文件
- Project Manager : 项目管理
- Prettier : 代码格式化

对于Vue开发者，推荐安装： Volar 

对于React开发者，推荐安装： ES7+ React/Redux/React-Native/JS snippets 


VSCode中的代码片段功能非常实用，可以在设置中搜索 `snippets` 进行配置，细节可以参考 <a href="https://juejin.cn/post/6844903869424599053" target="_blank">VSCode代码片段配置</a>

我们可以使用这个工具来方便地编写 JSON 配置文件： <a href="https://snippet-generator.app/" target="_blank">VSCode代码片段生成器</a>
{{< /hint >}}

### 任务 1

资源中的 `homework` 文件夹给出了一个模仿百度主页的网页（`index.html`），可是这个网页缺少了 CSS 和 JS 文件，你需要把附件文件夹中的 CSS 和 JS 代码引入到网页中

<span style="color: red">完成该环节的之后的网页截图</span>

### 任务 2

修改附件中的 `index.js`，使得点击搜索按钮后，浏览器会弹窗显示所搜索的内容。但是当搜索框为空的时候，点击搜索按钮后，浏览器会弹窗显示“请输入搜索内容”

<span style="color: red">搜索框为空的截图</span>

<span style="color: red">点击后的截图</span>

<span style="color: red">搜索框有内容的截图</span>

<span style="color: red">再次点击后的截图</span>

### 任务 3

修改 `index.html`，使 **热榜** 部分的样式其尽可能与下方相似，相关的图片放在了 `img` 文件夹下，其中把“《你的学号》”换成你真实的学号（例如 `21373000`），如有必要可以注释原有的代码，但不要删除，因为后续的任务还会用到

![image-20220321085947597](/SE-Labs/images/lab2/image-20220321085947597.png)

<span style="color: red">修改完的网页截图</span>

### 任务 4

修改 index.js，使得在点击 ID 为 top-right 的元素之后，会调用 clickLogin 函数

<span style="color: red">点击前的截图</span>

<span style="color: red">点击后的截图</span>

### 任务 5

点击登录按钮后，似乎用户已经正确地登录，但是页面似乎发生了一些错误。请尝试修改 `initUserInfo` 函数，使得用户登录后，页面显示依然正常。（使用审查元素分析网页变化）

{{< hint info >}}
作为开发者，不能信任任何用户可以编辑的内容，防止<a href="https://juejin.cn/post/6844903685122703367" target="_blank">XSS攻击</a>

对于本任务来说，我们不允许用户输入任意的 HTML 代码 ( `innerHTML` ) ，而是只允许用户输入纯文本 ( `textContent` )
{{< /hint >}}

<span style="color: red">点击后审查页面变化截图</span>

<span style="color: red">解释出现错误的原因</span>

<span style="color: red">修复后登录截图</span>

{{< hint info >}}

修复后截图可以参考下面两个版本，只需实现一种效果即可

- 简单版

  ![answer2](/SE-Labs/images/lab2/answer2.png)

- 进阶版

  ![answer1](/SE-Labs/images/lab2/answer1.png)
{{< /hint >}}
### 任务 6

将你的代码提交至远程仓库，github 或者 gitee 均可（至少保留 1 周），并在实验文档中说明

### 附加任务（非强制）

这部分建议学有余力的同学看一看，可能需要你 **额外** 学习一些前端知识

- 在任务 2 的基础上，使用户在搜索框按下回车的时候也可以进行搜索，并且会跳转到百度对应的搜索页面（处理键盘事件，链接外部页面）

- 在任务 3 的基础上加上醒目的大图，尽可能与下图相似

  ![image-20220321090301004](/SE-Labs/images/lab2/image-20220321090301004.png)
  {{< hint info >}}
  里面最显眼的那张图片并 **不是** 一个正方形哦，是一个圆角矩形，而且你可以发现我们所提供的原图是 **没有左上角的 1 标志**，请思考如何引入
  {{< /hint >}}

- 观察 `index.html`，可以发现左上方的`<a>`标签的`href`特性中使用了 http 和 https 两种不同的协议，修改附件中的 `index.js` 和`style.css` ，使得鼠标悬停在使用 http 协议的`<a>`标签上时标签内容为红色

  ![hover](/SE-Labs/images/lab2/hover.png)

  ![hover2](/SE-Labs/images/lab2/hover2.png)
  {{< hint info >}}
  对于这个任务，希望同学们遵循各司其职原则，即尽可能少用 JS 来干扰 CSS/HTML。

  例如，更改元素的 `className` 就优于对 `style` 直接进行更改。

  事实上，通过 JS 更改页面的 DOM 元素的类名数组是很常见的实现 **页面交互改变样式** 的方式，比如说白天/夜间模式的切换。
  {{< /hint >}}

## 实验报告

填写 homework 中的实验文档，简要阐明你的思路。

## 提交方式

- 截止时间：**2023/3/25 晚 12 点**

- 提交方式：[软院云平台](https://scs.buaa.edu.cn/)

- 提交内容：完善后的实验文档，将其命名为：

  ```txt
  学号_姓名_第2次实验.docx/pdf
  ```
