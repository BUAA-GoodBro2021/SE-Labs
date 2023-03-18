---
title: 'Lab02 前后端基础Ⅰ'
weight: 200
---

# Lab02 前后端基础Ⅰ

本次实验内容为前后端基础，每位同学只需要完成前端或后端的作业内容，并提交相应的作业。

建议优先按照组内前后端分工，学习相应的方面，乐此不疲者欢迎全栈！当然，还是要说，真正的全栈不是说会一个前端框架，会一个后端框架就可以称自己是全栈了，且不说“会”和“熟练应用”之间那不言而喻的鸿沟，全栈要掌握的能力是不能被“技术框架”来量化的。在此提醒大家不要好高骛远，先在自己选择的领域扎实耕耘。

{{< hint info >}}
建议组内三位负责前端，两位负责后端。软工一的前端工作量远大于后端，一定要保证前端有足够的人手。
{{< /hint >}}

## 传送门

- 前端：[前端 HTML/CSS/JS](/SE-Labs/docs/labs/lab02/frontend_index/)
- 后端：[后端 Django 框架](/SE-Labs/docs/labs/lab02/backend_index/)

## 前后端简介

### 前后端不分离

通过浏览器访问网站链接时，后端提前渲染好页面，一般以模板为基础动态生成，返回给浏览器。

特点：前后端内容耦合到一起

![前后端不分离](/SE-Labs/images/lab2/前后端不分离.png)

### 前后端分离

前端负责页面显示，浏览器访问时，前端返回静态页面，后通过 JS 方法向后端发送请求、接收响应。

负责工作：

- 前端：与浏览器联系，负责渲染页面内容，跳转路由，存取浏览器缓存，与后端交互
- 后端：负责存取数据库信息，处理复杂数据，响应前端的请求（后端不需要关心页面）

![前后端分离](/SE-Labs/images/lab2/前后端分离.png)