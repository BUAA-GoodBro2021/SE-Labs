---
title: '前端实验指南'
weight: 2001
---

# Lab02 前端基础

## 实验目的

- 了解基础的HTML，CSS，JS语法
- 练习引入css、js代码
- 练习处理事件
- 练习修改页面样式
- 练习修改页面逻辑
- 练习使用浏览器控制台
- 回顾第1次实验课git的使用

## 资源链接

https://bhpan.buaa.edu.cn:443/link/3A508B02D5CE20902AE2983009CE5D1B

Valid Until: 2023-07-15 23:59

## 实验指南

1. 查看资源链接中的**前端入门基础.mp4**、**前端入门基础.pdf**
2. 学习JS可以参考链接中的三本电子书，网页版可以参考<a href="https://zh.javascript.info/" target="_blank">现代JavaScript教程</a>
3. 推荐使用Chrome浏览器进行开发，调试技巧可以参考<a href="https://www.frontendwingman.com/Chrome/" target="_blank">Chrome DevTools使用技巧</a>
4. 在前端的学习和开发过程中，建议你时常参考<a href="https://developer.mozilla.org/zh-CN/" target="_blank">✨✨MDN Web Docs✨✨</a>，这是前端开发的百科全书
5. 完成实验作业并于 3.25 日晚 12 点前提交至 <a href="https://scs.buaa.edu.cn/" target="_blank">软院云平台</a>

{{< hint info >}}
很多同学认为前端开发就是框架 + 组件库 + 搜索引擎。

熟悉框架语法并从组件库进行CV固然可以快速完成需求，但软工一作为一系列软件工程开发的开端，作为助教，我们还是希望同学们能在这几个月的学习过程中打好JS和CSS的基础，增加自己日后面对复杂需求时的底气，勿以浮沙筑高台。
{{< /hint >}}

## 实验作业

你可以在所给资源的homework文件夹中找到实验文档并填写
{{< hint info >}}
本次实验建议使用Live Server拓展，我们可以在项目中将其作为一个服务器实时查看所开发的项目的效果。

安装拓展后，对index.html右键选择Open with Live Server开启服务。

![Live Server](/SE-Labs/images/lab2/LiveServer.png)
{{< /hint >}}

### 任务1

资源中的homework文件夹给出了一个模仿百度主页的网页（index.html），可是这个网页缺少了 CSS 和 JS 文件，你需要把附件文件夹中的 CSS 和 JS 代码引入到网页中

<span style="color: red">完成该环节的之后的网页截图</span>

### 任务2

修改附件中的index.js，使得点击搜索按钮后，浏览器会弹窗显示所搜索的内容。但是当搜索框为空的时候，点击搜索按钮后，浏览器会弹窗显示“请输入搜索内容”

<span style="color: red">搜索框为空的截图</span>

<span style="color: red">点击后的截图</span>

<span style="color: red">搜索框有内容的截图</span>

<span style="color: red">再次点击后的截图</span>

### 任务3

修改index.html，使**热榜**部分的样式其尽可能与下方相似，相关的图片放在了img文件下，其中把“《你的学号》”换成你真实的学号（例如21373000），如有必要可以注释原有的代码，但不要删除，因为后续的任务还会用到

![image-20220321085947597](/SE-Labs/images/lab2/image-20220321085947597.png)

<span style="color: red">修改完的网页截图</span>

### 任务4

修改 index.js，使得在点击 ID 为 top-right 的元素之后，会调用 clickLogin 函数

<span style="color: red">点击前的截图</span>

<span style="color: red">点击后的截图</span>

### 任务5

点击登录按钮后，似乎用户已经正确地登录，但是页面似乎发生了一些错误。请尝试修改 initUserInfo 函数，使得用户登录后，页面显示依然正常。（使用审查元素分析网页变化）

<span style="color: red">点击后审查页面变化截图</span>

<span style="color: red">解释出现错误的原因</span>

<span style="color: red">修复后登录截图</span>

### 任务6

将你的代码提交至远程仓库，github或者gitee均可（至少保留1周），并在实验文档中说明

### 附加任务（非强制）

这部分建议学有余力的同学看一看，可能需要你**额外**学习一些前端知识

- 在任务2 的基础上，使用户在搜索框按下回车的时候也可以进行搜索，并且会跳转到百度对应的搜索页面（处理键盘事件，链接外部页面）

- 在任务3的基础上加上醒目的大图，尽可能与下图相似

  ![image-20220321090301004](/SE-Labs/images/lab2/image-20220321090301004.png)
  {{< hint info >}}
  里面最显眼的那张图片并**不是**一个正方形哦，是一个圆角矩形，而且你可以发现我们所提供的原图是**没有左上角的1标志**，请思考如何引入
  {{< /hint >}}

- 观察index.html，可以发现左上方的`<a>`标签的`href`特性中使用了http和https两种不同的协议，修改附件中的index.js和style.css，使得鼠标悬停在使用http协议的`<a>`标签上时标签内容为红色

  ![hover](/SE-Labs/images/lab2/hover.png)

  ![hover2](/SE-Labs/images/lab2/hover2.png)
  {{< hint info >}}
  对于这个任务，希望同学们遵循各司其职原则，即尽可能少用JS来干扰CSS/HTML。

  例如，更改元素的className就优于对style直接进行更改。
  {{< /hint >}}

## 实验报告

填写homework中的实验文档，简要阐明你的思路

## 提交方式

- 截止时间：**2023/3/25 晚12点**

- 提交方式：[软院云平台](https://scs.buaa.edu.cn/)

- 提交内容：完善后的实验文档，将其命名为：

  ```txt
  学号_姓名_第2次实验.docx/pdf
  ```
