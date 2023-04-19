---
title: 'CI/CD 简介'
weight: 2001
---

# Lab07 CI/CD 简介

## CI/CD 基本概念

**CI/CD** 指的是**持续集成**(Continuous Integration)、**持续交付**(Continuous Delivery)和**持续部署**(Continuous Deployment)。

![CI/CD 图解](/SE-Labs/images/lab7/ci_cd.jpg)

在软件开发过程中，会经历开发、构建、测试、发布、部署等过程，在产品的**迭代**过程中，这些过程会不断地重复进行。

现在试想一下，你是一名**测试人员**，已经写好了很多测试用例，但是**开发人员**每次更新代码你都要手动重新构建软件，运行所有的测试用例并给出反馈，这是非常痛苦的。

CI/CD 就是将这些过程**自动化**的工具或者服务，请阅读这一篇[知乎文章](https://zhuanlan.zhihu.com/p/422815048)了解更详细的信息。

简单来说，可以认为如下的观点是正确的：

- 持续集成：自动化地进行软件**构建**(Build)、**测试**(Test)、**代码合并**(Merge)
- 持续交付：自动化地进行软件代码的**发布**(Release)，发布的代码可以稳定地在生产环境中使用
- 持续部署：自动化地进行软件的**部署**(Deploy)，将代码库中的代码实际部署到生产环境中

## 常用的 CI/CD 工具

CI/CD 的工具可以说是**数不胜数**，有无数种方案可以实现 CI/CD 的工作流。

根据项目的不同，选择的 CI/CD 工具很可能会**不一样**，这里简单地列出一些 CI/CD 工具：

- **Github Actions**
- Jenkins
- Circle CI
- Gitlab CI
- Bitbucket Pipelines
- Azure DevOps

当需要用到这些工具的时候，再去查阅相关的**官方文档**就可以了，软件开发不就是看文档写文档嘛，有什么难的（bushi

## 大作业 CI/CD 推荐方案

{{< hint info >}}
虽然大作业**不强制要求**部署到云服务器上，但是我们建议每个小组都购买一台云服务器，并且实现在云服务器上部署你们的网站。一些云服务器可以**按小时计费**，最基础的云服务器**包年**大概在**100 元**左右(学生价)。
{{< /hint >}}

我们推荐在 **Github** 上实现大作业前后端的 CI/CD，前后端各自一个仓库，两个仓库采用各自的 CI/CD 工作流。在向仓库的 main 分支 push 之后，利用 Github Actions 自动化地实现前后端项目在云服务器上的自动部署。

关于 Github Actions 的简单介绍，可以看看[这篇博客](https://matrix53.github.io/2021/07/25/Github%E6%8E%A2%E7%A7%98/)。

## 实验作业

部署自己的**个人博客**！

{{< hint info >}}
CI/CD 的实验作业将仅涉及到 **CD** 的内容，使用 [Hugo](https://gohugo.io/) 作为博客框架，使用 [PaperMod](https://github.com/adityatelange/hugo-PaperMod) 主题，部署的个人博客在所有截图完成后可删除(当然也可以保留)
{{< /hint >}}

{{< hint danger >}}
- 如果已经有同学实现了**大作业**的 CI/CD，那么你的 CI/CD 作业可以**不用写**，但是需要提交你大作业的**自动化部署方案**，即你是如何利用 Github Actions 之类的工具实现自动化的
- 如果有同学已经有了**个人博客**，且已经实现了个人博客的**自动化部署**，那么可以提交你自己的个人博客的 CD 方案，这种情况也不用完成本文接下来的内容
{{< /hint >}}

{{< hint warning >}}
作业命名为**CI_CD_个人博客.pdf**或者**CI_CD_大作业.pdf**，建议使用 Markdown 编写然后导出 pdf
{{< /hint >}}

### 环境配置

{{< hint info >}}
这一部分内容适用于**想要保留**个人博客的同学，不想保留的可以 **fork** [这个仓库](https://github.com/Super-BUAA-2021/myblog)到自己的 Github 账户下，并**直接跳过**环境配置这一部分
{{< /hint >}}

#### 安装 Hugo

> 官方安装文档：https://gohugo.io/getting-started/installing/

{{< tabs "1" >}}
{{< tab "MacOS" >}}
使用 **Homebrew** 安装：`brew install hugo`

使用 **MacPorts** 安装：`port install hugo`
{{< /tab >}}
{{< tab "Linux" >}}
在 **Ubuntu** 下：`sudo apt install hugo`

在 **Arch Linux** 下：`sudo pacman -Syu hugo`
{{< /tab >}}
{{< tab "Windows" >}}
1. 下载 [hugo_0.98.0_Windows-64bit.zip](https://github.com/gohugoio/hugo/releases/download/v0.98.0/hugo_0.98.0_Windows-64bit.zip)
2. 解压该zip文件，将**hugo.exe**移动到一个合适的目录(例如D:\Hugo)
3. 将hugo.exe所在的**目录**(例如D:\Hugo)加入到**系统环境变量**中
{{< /tab >}}
{{< /tabs >}}

#### 创建个人博客

> Hugo 官方文档：https://gohugo.io/documentation/

打开你的 **Terminal**，将**工作目录**切换到工作区(下文中以D:\Workspace代替)：`cd D:\Workspace`

使用 Hugo 生成**新站点**：`hugo new site blog -f yml`

现在，你的个人博客就创建好了，位于`D:\Workspace\blog`下

#### 使用 PaperMod 主题

{{< hint info >}}
使用别的主题也可以，**但是**要在提交的作业中说明
{{< /hint >}}

> PaperMod 主题官方文档：https://github.com/adityatelange/hugo-PaperMod

将工作目录切换到**个人博客**下：`cd D:\Workspace\blog`

初始化 **Git** 仓库：`git init`

使用 **PaperMod** 主题：`git submodule add --depth=1 https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod`

在`D:\Workspace\blog\config.yml`中添加这一行(更详细的配置参见**Hugo框架**以及**PaperMod主题**的官方文档)：

```yml
theme: "PaperMod"
```

#### 第一篇文章

将工作目录切换到**个人博客**下：`cd D:\Workspace\blog`

**创建**一篇新文章：`hugo new posts/my-first-post.md`

编辑`D:\Workspace\blog\content\posts\my-first-post.md`，将其内容**修改**为：

```markdown
---
title: "My First Post"
date: 2022-05-04T13:25:38+08:00
draft: false
---
我的第一篇博客
```

启动 Hugo 服务器**查看**当前的博客效果：`hugo server`

服务器运行**成功后**，可以在`http://localhost:1313`查看博客效果，例如下图：

![第一篇博客](/SE-Labs/images/lab7/blog1.png)

#### 博客的美化

这部分内容不做要求，将不再展开讲解，有兴趣的同学可以自行查阅[PaperMod主题的文档](https://github.com/adityatelange/hugo-PaperMod/wiki/Features)进行配置，PaperMod主题还有一个[示例的博客网站](https://adityatelange.github.io/hugo-PaperMod/)以供参阅，实际配置起来并不复杂。

{{< hint info >}}
对于喜欢折腾个人博客的同学来说，可以参考<a href="https://anzhiy.cn/posts/sdxhu.html" target="_blank">butterfly 重装日记</a>，演示效果如下。
<iframe src="//player.bilibili.com/player.html?aid=556933559&bvid=BV13v4y1c75G&cid=800077849&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true" style="margin:auto;"> </iframe>
{{< /hint >}}

### 启用 Github Pages

关于 Github Pages，这里有一篇[博客](https://matrix53.github.io/2021/07/25/Github%E6%8E%A2%E7%A7%98/)可以作为简单的参考

#### 创建个人博客仓库

{{< tabs "2" >}}
{{< tab "跳过了环境配置看这里" >}}
除了fork[这个仓库](https://github.com/Super-BUAA-2021/myblog)之外不需要做任何事
{{< /tab >}}
{{< tab "没有跳过环境配置看这里" >}}
1. 在Github上**新建**一个仓库(名字叫myblog或者blog之类的，下文假设为myblog)，最好是public的仓库，例如下图的配置：
![博客仓库配置](/SE-Labs/images/lab7/blog2.png)
2. 根据Github的提示，将本地的`D:\Workspace\blog`仓库push到远程仓库，例如下图中的红色方框所示：
![推送到远程](/SE-Labs/images/lab7/blog3.png)
{{< /tab >}}
{{< /tabs >}}

创建好仓库之后，结果应该如下图所示：
![初始化博客仓库](/SE-Labs/images/lab7/blog4.png)

#### 创建username.github.io仓库

为了使用 Github Pages，该仓库是必须要创建的，这里的**username是你的Github用户名**，例如下图：
![初始化仓库](/SE-Labs/images/lab7/blog5.png)

至此，你已经有了两个仓库，即`myblog`和`username.github.io`

{{< hint danger >}}
将这两个仓库目前的**内容**截图，作为作业的**第一张截图**
{{< /hint >}}

### 添加 CD 工作流

#### 博客仓库的配置

在远程仓库上**新建**一个名为`gh-pages`的分支，如下图所示：
![新建分支](/SE-Labs/images/lab7/blog8.png)

在博客仓库的`Settings -> Actions -> General`中**修改**如下配置，使得 Github Actions 拥有对仓库的写权限，如下图所示：
![修改配置](/SE-Labs/images/lab7/blog12.png)

接下来**查看**`Settings -> Pages`下的内容，就会发现Github Pages**已经启用了**，例如下图：
![成功启用](/SE-Labs/images/lab7/blog11.png)

{{< hint info>}}
如果没有启用，需要检查自己曾经是否进行过`username.github.io`仓库或其他仓库的Github Pages配置，并对其进行`Unpublish site`操作。
{{< /hint >}}

{{< hint danger >}}
将Github Pages成功启用的**页面**截图，作为作业的**第二张截图**
{{< /hint >}}

#### 配置文件的编写

为了使用 Github Actions，我们需要在博客仓库中创建`.github/workflows`文件夹，如下图所示：
![创建文件夹](/SE-Labs/images/lab7/blog6.png)

在该文件夹中的`yml`文件将成为我们定义的CI/CD工作流，下面我们在`.github/workflows`中创建一个`gh-pages.yml`文件，如下图所示：

  ![新建工作流](/SE-Labs/images/lab7/blog7.png)

`gh-pages.yml`文件的内容为：
```yml
name: github pages

on:
  push:
    branches:
      - main  # Set a branch to deploy
  pull_request:

jobs:
  deploy:
    runs-on: ubuntu-20.04
    steps:
      - uses: actions/checkout@v2
        with:
          submodules: true  # Fetch Hugo themes (true OR recursive)
          fetch-depth: 0    # Fetch all history for .GitInfo and .Lastmod

      - name: Setup Hugo
        uses: peaceiris/actions-hugo@v2
        with:
          hugo-version: 'latest'
          # extended: true

      - name: Build
        run: hugo --minify

      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        if: github.ref == 'refs/heads/main'
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./public
```

{{< hint info >}}
下面是具体步骤的解释：
- `uses: actions/checkout@v2`: 使用 GitHub 官方的 `actions/checkout Action` 操作，用于将代码检出到 Workflow 的 Runner 中。`submodules: true` 会把 Hugo 的主题一起检出，`fetch-depth: 0` 会将所有历史记录都检出到 Runner 中，以便 Hugo 可以找到 .GitInfo 和 .Lastmod 文件。
- `name: Setup Hugo`: 指定这个步骤的名称，这里是设置 Hugo。使用 `peaceiris/actions-hugo` Action 操作，用于在 Workflow 的 Runner 中安装 Hugo。
- `hugo-version: 'latest'`: 指定要安装的 Hugo 版本，这里是最新版本。
- `run: hugo --minify`: 构建站点并将其压缩，减小文件大小并加快网站加载速度。
- `name: Deploy`: 指定这个步骤的名称，这里是部署。使用 `peaceiris/actions-gh-pages` Action 操作，将构建好的 Hugo 站点发布到 GitHub Pages，这里是发布到 `gh-pages` 分支。
- `if: github.ref == 'refs/heads/main'`: 只有在 Push 到 `main` 分支时才会运行此步骤。
- `github_token: ${{ secrets.GITHUB_TOKEN }}`: 指定 GitHub Personal Access Token，用于发布网站到 GitHub Pages。
- `publish_dir: ./public`: 指定要发布的目录，这里是 `./public` 目录，它是 Hugo 生成的静态 HTML 文件所在的目录。
{{< /hint >}}

{{< hint info >}}
 `GITHUB_TOKEN` 是GitHub官方提供的一个**特殊的**token，用于代表 GitHub Actions 进行身份验证，不需要自己创建。更多信息可以参考<a href="https://docs.github.com/zh/actions/security-guides/automatic-token-authentication" target="_blank">自动令牌身份验证</a>。
{{< /hint >}}


{{< hint info >}}
另外，为了博客网站的**正常展示**，**还需要**将`config.yml`中的**baseURL**更改为这样的格式：
`https://<USERNAME>.github.io/<REPOSITORY_NAME>`

最后的`config.yml`文件大概如下所示(**用户名和仓库名称用自己的**)：
```yml
baseURL: https://llleoli.github.io/myblog/
languageCode: en-us
title: My New Hugo Site
theme: "PaperMod"
```
{{< /hint >}}

最后，将博客仓库中新增的更改**push到远程**，CI/CD 的工作流就**已经实现了**。

{{< hint danger >}}
将目前博客远程仓库中的**内容**截图，作为作业的**第三张截图**
{{< /hint >}}

### 结果验证

访问自己的博客网站，**查看**网站效果，如下图所示：
![查看效果](/SE-Labs/images/lab7/blog13.png)

{{< hint danger >}}
将自己博客的**网址和内容**截图，作为作业的**最后一张(第四张)截图**
{{< /hint >}}

**好了**，到目前为止，你已经有了一个可以访问的**个人博客**了！如果想了解更多Github Actions的信息，建议去阅读官方文档，**没有什么东西比官方文档更好用了**。
