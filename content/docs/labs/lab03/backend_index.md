---
title: '后端实验指南（修订中...）'
weight: 2002
---

# Lab03 后端进阶

## 前情提醒

大家目前接触过的 java 大部分属于 javaSE 部分，而后端框架一般属于 javaEE 部分，javaSE 和 javaEE 二者之间的区别还是很大的，而且 SpringBoot 该框架要求的前置知识较多，因为SprintBoot 是 Spring 全家桶的整合，需要了解 Spring，SpringMVC，MyBatis（MyBatis-plus）三件套的基本知识，同时在面对增删改查的复杂逻辑时需要手写 SQL 语句，所以不太适合后端新手同学使用该框架作为后端框架的入门。

因此该后端实验有很多实验是<span style="color: red">选做（标红的都是选做——高手可以尝试）</span>部分，不太要求同学们完全掌握这门框架，目前只需要根据教学视频对于该框架有一个初步的了解即可。

如果在SpringBoot上遇到什么问题可以先尝试自己解决（因为Zhoues也不太熟），如果真的遇到的问题，可以请教群里面的SpringBoot大神，当然还是建议花更多的时间在 Django 上！

## 实验目的

- 学习使用maven管理配置依赖
- 了解springboot的基础知识，能够自行创建一个springboot项目
- 了解基础的分层结构
- 【<span style="color: red">高手必须掌握的</span>】锻炼解决问题的能力，通过查询**官方文档**或其他**技术博客**解决遇到的问题

## 资源链接

https://bhpan.buaa.edu.cn:443/link/3A508B02D5CE20902AE2983009CE5D1B</a>

Valid Until: 2023-07-15 23:59

## 实验指南

- 阅读资源中提供的Maven资料，了解Maven的基础内容，如果你还不了解基础的java依赖引入，可以先行学习，再来学习Maven
- 学习《Springboot基础》与视频资料，自行创建一个基础的Springboot项目并成功运行
- 学习使用 postman/apifox（可参考官网教程<a href="https://learning.postman.com/docs/getting-started/introduction" target="_blank">https://learning.postman.com/docs/getting-started/introduction</a>，或者 https://www.apifox.cn/help/ 不推荐一口气读完，推荐随用随查）

## 实验作业

### 任务1

提供视频中的基础代码(跟视频手打or自己弄明白原理手搓)，并连接自己的本地数据库（需要回忆你的数据库课程知识），并且成功运行，请提供运行**截图**

### 任务2<span style="color: red">（考虑到大多数同学都是初学javaEE，本任务不再强行要求，高手们可以尝试）</span>

根据注册代码和 session 的处理方式完成登录请求（localhost:8090/login），并使用Postman / ApiFox 测试，请提供运行**截图**

{{< hint info >}}
温馨提示：session 的处理方式 ppt 上所说的是绝对不够用的，这里是为了考验大家能不能通过官网等渠道获取到有用信息
{{< /hint >}}

### 任务3

增加个人信息查询功能（localhost:8090/show_info），并使用 Postman/ApiFox 测试（在 body 中返回“name”：“xxx”， “password”： “xxx”），请提供运行**截图**

写一份实验报告，简要说明任务 1 的完成过程，以及在任务 2 和任务 3 中使用 Postman/ApiFox 测试情况截图（测试数据和结果），最好附上你的心得

{{< hint info >}}

注：完成上述需求并且运行无 bug 和报错即满分。

{{< /hint >}}

##### 提交方式

- 截止时间：**2023/3/31 晚12点**
- 提交方式：<a href="https://scs.buaa.edu.cn/" target="_blank">软院云平台</a>
- 提交内容：实现上述任务1和3功能后的项目代码文件夹<span style="color: red">（高手可以提供任务2）</span>，和实验报告，命名格式如下：


```txt
学号_姓名_第3次实验.zip
|-- 项目代码文件夹
 -- 学号_姓名_第3次实验_实验报告.docx/pdf
```

