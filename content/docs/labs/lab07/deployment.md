---
title: '前后端项目部署'
weight: 2002
---

# Lab07 前后端项目部署

## 实验指南

结合所给的PPT（服务器部署Vue和Django项目.pptx），观看服务器部署视频教程。

视频包含完整的服务器部署过程，前端的同学可根据**PPT上的视频时间节点信息**选择跳过某些片段，当然也可以尝试理解理解，或者略看一下。

除了所给的视频和PPT之外，也可以参考下面热心学长的项目部署全流程总结。

## 具体流程

1. 服务器预设置（SSH远程连接、添加用户、配置公钥）
2. 安装远程数据库（可选）
3. 安装Django环境（MiniConda）
4. 配置uWSGI
5. 配置Nginx

## 资源汇总

- 部署全流程：<a target="_blank" href="https://bhpan.buaa.edu.cn/#/link/3A508B02D5CE20902AE2983009CE5D1B?gns=24318D92FBF14A4F975E41AFE116650E%2F6478CDA2F8744418AA85680FAAE0D5D6%2F4BF16FA615C64D0896B8FFFC6E1210B7%2F4452E6590A644E26A42CC13790BB0A77%2FAF89FB962B4A4328ACE13934D37BC740">热心学长的项目部署全流程总结</a>
- Tmux 教程：<a target="_blank" href="https://www.ruanyifeng.com/blog/2019/10/tmux.html">https://www.ruanyifeng.com/blog/2019/10/tmux.html</a>
- Miniconda安装教程：<a target="_blank" href="https://os.51cto.com/article/636125.html">https://os.51cto.com/article/636125.html</a>

## 注意事项

- 如果需要在本地运行提供的 frontend_demo，请记得先 `npm install` 安装依赖
- 提供的 demo 采用 vue2 + Django v3.2 版本


## 实验作业

{{< hint danger >}}
本次部署作业为小组作业，仅要求小组组长提交一份实验报告。

如果你们小组已经部署好了项目，仅需在报告中展示一些重要的服务器配置文件截图，并结合简要的文字说明，最后附上可访问的网站链接。
{{< /hint >}}

本次部署作业，要求在小组的服务器上，完成部署前端**和**后端任务。部署的项目可以使用提供的 frontend_demo 和 backend_demo，也可以使用大作业项目。

实验报告命名要求：前后端部署报告.pdf

### 部署前端

在服务器或虚拟机上部署前端项目，不要求能与后端正常交互（能实现当然更好）。要求部署的前端页面中含有自己的学号和姓名标识。

实验报告中需包含 Nginx 配置文件内容截图、浏览器通过 IP 访问前端项目的截图等**能够证明你成功部署的图片和文字说明**，同时需附上可访问的 IP 地址或链接。

### 部署后端

在服务器或虚拟机上部署后端项目。

实验报告中需包含后端运行证明截图（如 Tmux 运行截图、uWSGI 日志截图等）、Nginx 配置文件内容截图、Postman 向服务器 IP 加端口发送请求并成功响应的截图（要求请求信息含自己的学号和姓名标识）等**能够证明你成功部署的图片和文字说明**，同时需附上可访问的 IP 地址或链接。