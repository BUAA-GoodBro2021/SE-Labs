---
title: 'Vue 创建项目'
weight: 20032
---

# Vue 创建项目

## 安装 vue 环境

在配置好 npm 环境后，我们就可以开始着手创建我们的第一个 vue 项目了。不过不要着急，在创建之前，我们还需要把 vue 相关的依赖环境安装到全局目录。vue.js 作为 vue 运行的核心部分，肯定是不可或缺的；而无论是 vue2 还是 vue3，现在主流的构建方式离不开官方的脚手架 vue-cli；此外，但凡是一个多页面项目，都离不开前端路由的架构设计。因此 vue-router 也几乎是任何 vue 项目不可或缺的一部分。

输入以下命令，安装 vue.js、vue-router、vue-cli 脚手架到 global 全局目录：

```shell
npm install vue -g
npm install vue-router -g
npm install -g @vue/cli
```

Vue CLI 4.x 需要 Node.js v8.9 或更高版本 (推荐 v10 以上)。

## 创建 vue 项目并配置

使用 vue-cli 创建 vue 项目：
```shell
vue create vue-project      # [vue-project] 为项目名称
```

此时窗口如下：

![step1](/SE-Labs/images/lab3/step1.png)

同学们由于是第一次创建 vue 项目，应该没有第一项。事实上第一项是个性化设置的一个保存，以便下一次创建项目时，“一键导入个性化配置”来创建项目。大家可以看出来，默认的 vue2 和 vue3 项目配置是没有 vuex 和 router的。这意味着如果按照这 2 个模板去创建项目，之后是需要执行 npm 安装命令手动导入的。

{{< hint warning >}}
由于 vue2 和 vue3 存在差异，众多工具库也进行了大版本更新，vuex 和 vue-router 默认下载后对应的版本是 4，和 vue3对应，如果说是在 vue2 项目创建时没有选择 vuex 和 router，那么就需要后续执行 npm 安装命令，此时要精确安装到对应版本。安装对应到 vue2 的两个库命令如下：
```shell
npm i vuex@3 --save
npm install vue-router@3 --save
```
{{< /hint >}}

绝大多数情况下，我们在 vue-cli 提供的两个默认模板中选择一个即可。指导书这里带着大家选择最后一项，手动配置需求来打造自己的 vue 项目模板。选择后进入以下页面：

![step2](/SE-Labs/images/lab3/step2.png)

上面的英语指导已经说的很明显了，这里介绍一下这些选项的含义：

- Babel：Babel 编译
- TypeScript：TypeScript 支持
- Progressive Web App (PWA) Support：PWA 支持
- Router：Vue 路由，这里就是指 Vue-Router
- Vuex：Vue 状态管理
- CSS Pre-processors：CSS 预编译器（包括：SCSS/Sass、Less、Stylus）
- Linter / Formatter：代码检测和格式化
- Unit Testing：单元测试
- E2E Testing：端到端测试

一般来说，vue 项目常用的就是 vuex 和 router，vue3 项目视情况会加入 TypeScript 支持。以及如果希望采用比 CSS 更高级的样式语言，则需要配置 CSS 预编译器。但是，这些都可以不在这里选择，而是在项目需要时再使用 npm 安装命令（不然 vue-cli 也不会提供只含有 babel 和 eslint 的空白模板了）。前端单元测试是进阶的要求，在大体量的项目中，前端单元测试是不可或缺的。常用的单元测试解决方案是 Jest。这个 vue 和 react 均通用。

选好配置模板后，接下来选择创建 vue2 项目还是 vue3 项目。我们这里先以 vue2 为例。

![step3](/SE-Labs/images/lab3/step3.png)

下一个选项是选择 router 的模式是否为 history 模式。前端路由模式主要分为 Hash 和 History 两种模式，前者拥有更好的兼容性，但是会使得路由中多一个 #。在 IE 浏览器退出历史舞台的今天，我们一般选择 History 模式就足够了。关于两种模式，同学们在学习 vue-router 时会具体了解。

![step4](/SE-Labs/images/lab3/step4.png)

接下来是选择 ESLint 的代码规范，这里选择 ESLint + Standard config。其他选项感兴趣的同学可以自行查找。其中 prettier 也是很有名的代码规范辅助工具，VS Code 上有对应的插件。进行代码规范是在企业级别的项目中必不可少的一环，试想一下，如果说一个项目中，开发团队中的每一个程序员都按照自己的习惯来进行编程，那么最后整个项目的代码风格千奇百怪，不仅不雅观，更为后续的维护和迭代带来了极大的困难。我们这里的 ESLint 起不到如此具体的限制（比如缩进是几个空白符，行末是否要添加分号等），更多地是在检测到一些明显的语法错误时提醒开发者。

![step5](/SE-Labs/images/lab3/step5.png)

接下来选择进行 ESLint 检查的时机。这里没有特殊要求，看自己的需求。
- Lint on save：在保存时进行检测
- Lint and fix on commit：在fix和commit时进行检查

![step6](/SE-Labs/images/lab3/step6.png)

选择 Babel，ESLint（如果选择了CSS预处理器，这里还有 PostCSS）等配置文件的存放位置。这里一般选择 In dedicated config files。
- In dedicated config files：单独保存在各自的配置文件中
- In package.json：保存在package.json文件中

最后，个性化配置完毕，我们可以选择是否保存这一次的配置。如果选择 N，那么只会根据这套方案配置一次项目。如果选择 Y，那么还需要输入自己为这套方案定下的名字，这样在下次创建项目时，以这个名字命名的项目配置方案就会出现在选项中。

![step7](/SE-Labs/images/lab3/step7.png)

有些情况下还会遇到选择包管理器（package manger），这里对于 pnpm 和 npm 不做过多介绍，感兴趣的同学可以查看 [pnmp 中文文档](https://www.pnpm.cn/)

![step8](/SE-Labs/images/lab3/step8.png)

选择之后按下 enter，就可以看到项目正在快速搭建了。

![step9](/SE-Labs/images/lab3/step9.png)

最后的最后，看到如下场景，说明我们已经成功创建了想要的 vue 项目。输入 `cd vue-project` （项目名），进入项目目录。

![step10](/SE-Labs/images/lab3/step10.png)

#### 本地运行项目

执行 `npm run serve`，就可以看到项目在 8080 端口运行起来了。成功运行后，访问 http://localhost:8080/ 即可看到 vue 项目的默认界面。

![step11](/SE-Labs/images/lab3/step11.png)

![step12](/SE-Labs/images/lab3/step12.png)

>如果 8080 端口被占用，这里的端口可能会改变，实际以终端提示为主

#### 打包部署到服务器上

执行 `npm run build`，就可以看到项目被打包成了一个新的文件夹，里面的 CSS 和 HTML 文件均被压缩了。这里不做展开介绍，后续的 lab 中会教授大家部署项目的方法。


## Vue 新推出的创建工具 create-vue

从名字上看，很难说和 **创建 react 项目的工具 create-react-app** 没有关系。create-vue 是 vue 官方最近推出的 vue 项目创建工具。

确保你安装了最新版本的 Node.js，然后在命令行中运行以下命令
```shell
npm init vue@latest
```
![pinia](/SE-Labs/images/lab3/pinia.png)

可以看到，上面列出的全都是 vue 升级到 Vue3 后拥抱或者提高支持度的新技术，TypeScript，JSX，Vite…… 可以说，官方在考虑在未来用 `create-vue` 来代替 `vue-cli` 脚手架。更多的详细信息参见 <a href="https://cn.vuejs.org/guide/quick-start.html" target="_blank">https://cn.vuejs.org/guide/quick-start.html</a>

虽然如此，`vue-cli` 仍然是目前最常用的 vue 创建脚手架，且无论采用哪种方式，创建的 vue 项目是没有本质区别的。
