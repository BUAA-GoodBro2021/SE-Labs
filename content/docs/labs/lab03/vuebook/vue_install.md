---
title: 'Vue 安装'
weight: 20031
---

# Vue 安装

使用 Vue.js 的方式有很多，包括直接用 script 标签引入、使用 CDN 方法引入、NPM 方法安装等。在一般较大的项目开发中，都会采取后者，这里也仅对 NPM 安装方式进行介绍。

在安装 NPM 前，我们首先需要准备好 Node.js 环境。Node.js 是一个基于 Chrome V8 引擎的 JavaScript 运行环境，使得 JavaScript 可以脱离浏览器运行。 NPM 是 Node.js 自带的包管理器，具备命令行接口和软件注册中心 (registry)，使用 NPM 可以安装、管理、运行 packages，为项目代码适配 packages 等。本教程常用的是用它来安装环境包（如 vue-cli），以及运行 vue 等前端项目（npm run serve）。

下载 NPM，有两种方法，直接下载使用一个特定版本的 Node.js，或安装 NVM（npm version manager）可管理多个 Node.js 版本环境。本教程推荐的是使用 NVM 安装。原因是 Node.js 版本更新快，向前兼容性较差，很容易发生平时使用的版本无法安装某个插件环境的情况。比如 v14 安装了 vue 环境，此时想在本地安装 gitbook 环境，发现很多插件要求 v10，如果采用的单一版本就无法使用这些插件。而 nvm 就是类似 conda 的 Node.js 环境管理器，允许在一台机器拥有多个 Node.js 和 NPM 版本环境。

注意：在团队中一定要尽量统一环境，不然很可能会因为兼容性差异造成各种稀奇古怪的问题。在正式的项目开发中，Node.js 和 NPM 版本、开发框架版本、Git 提交规范、代码格式规范等都是要事先规定好的。

{{< hint info >}}
不想采用 NVM 安装方法，文末有推荐直接安装 NPM 的博客链接
{{< /hint >}}

## 下载 NVM

{{< hint warning >}}
若本地有 Node.js 环境，下载 NVM 前需先卸载！
{{< /hint >}}

第一步，下载最新版 NVM ，链接如下：

1. Windows 版本：<a href="https://github.com/coreybutler/nvm-windows/releases" target="_blank">https://github.com/coreybutler/nvm-windows/releases</a>，下载 nvm-setup.zip

2. Mac 版本：<a href="https://github.com/nvm-sh/nvm#install--update-script" target="_blank">https://github.com/nvm-sh/nvm#install--update-script</a>

**注意安装路径不能出现中文和空格**

nvm 安装路径示例

![nvm-address](/SE-Labs/images/lab3/nvm-address.png)

npm 安装路径示例

![node-address](/SE-Labs/images/lab3/node-address.png)

安装完成后，输入下列命令验证是否安装成功：

```shell
nvm --version
```

接下来，由于从 npm 官方获取 npm 包可能偶尔会因为网络问题导致失败，我们这里将 npm 包的下载源地址更改为淘宝镜像。打开 nvm 安装文件夹，在文件夹下的 settings.txt 文件中添加：

```shell
node_mirror: http://npm.taobao.org/mirrors/node/
npm_mirror: https://npm.taobao.org/mirrors/npm/
```

![nvm-setting](/SE-Labs/images/lab3/nvm-settings.png)

当然，如果说不愿意直接改配置文件，也可以通过 nrm 的方式来管理 npm 镜像源。nrm（npm registry manager）是 npm 的镜像管理工具，使用它可以快速地在 npm 源间切换。

在命令行执行命令，`npm install -g nrm`，全局安装 nrm。执行命令 `nrm ls` 查看可选的源。如果要切换到 taobao 源，执行命令 `nrm use taobao`。

![nrm](/SE-Labs/images/lab3/nrm.png)


## NVM 常用命令

一些实用的 nvm 命令如下：

```shell
nvm --version               # 查看nvm版本
nvm install latest          # 安装最新版 Node.js
nvm install <version>       # 安装指定版本 For examle:
nvm install v14.16.0
nvm ls                      # 查看已安装的 Node.js 版本
nvm use v14.16.0            # 切换使用 v10.13.0 版本
nvm alias default 14.16.0   # 设置默认版本
```

## 使用 NVM 安装 Node.js

使用 `nvm install` 命令安装 Node.js，这里以 14.16.0 版本为例：

```shell
nvm install v14.16.0
```

等待较短时间后，即安装成功。接下来，在 **确保自己是以管理员身份打开 cmd 的前提下** 输入：

```shell
nvm use v14.16.0
npm --version
```

出现版本号即说明 npm 安装成功。v14.16.0 版本的 Node.js 对应的 npm 版本应该是 6.14.11。每个 Node.js 的版本都对应管理了指定 npm 版本，他们之间的对应关系可以在 node.js 的官网查到。

注意：这里虽然是按照 v14.16.0 这个公认的稳定版本带大家进行设置，但是其对应的 npm 版本是相对较老的。在 npm 7 版本进行了较大的改动，突出表现为 `lockfileVersion@1` 和 `lockfileVersion@2` 的不同。因此，建议大家组内统一 npm 版本，否则会造成不必要的麻烦。

## 后言
如果不想采用本文章所讲的『Nvm管理和Npm安装』的方式，可以参考以下链接直接安装 NPM：

<a href="https://www.liaoxuefeng.com/wiki/1022910821149312/1023025597810528" target="_blank">安装Node.js和npm - 廖雪峰的官方网站</a>

<a href="https://www.runoob.com/vue2/vue-install.html" target="_blank">Vue.js 安装 - 菜鸟教程</a>