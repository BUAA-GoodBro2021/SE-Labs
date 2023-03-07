---
title: 'Git 简易教程'
weight: 1001
---

# Git 指南

{{< hint info >}}
本教程涉及命令行指令说明时，`[]` 表示该参数为可选，`<>` 仅说明参数意义，需根据实际来定义
{{< /hint >}}

## Git 简介

Git 是一个开源的分布式版本控制系统，用于敏捷高效地处理或大或小的项目。利用 git，可以在本地很好地控制项目版本，让项目有条不紊地进行，编写代码错误还能通过回退进行纠正；通过提交、拉取、推送等操作，与队友或同事参与远程共同开发。

为什么我们需要 git？试想一下，在面对一个万行级别甚至更高级别的项目时，单个程序员已经很难完成和掌控整个项目。此时扮演对项目进行开发和维护角色的往往是一个多人团队。事实上，无论是开发阶段还是维护阶段，每个人所熟悉的也只是自己负责的那部分代码而已。在团队开发中，每个开发者都在自己负责的部分编写了不同的代码，很多情况下甚至在同一个文件做了不同的修改。如何把大家的汗水与智慧的结晶进行版本管理，综合为一个完整且稳定的项目？

在过去，需要分配专门的人员完成这种统筹兼顾的工作。但是现在，以 git 为代表的分布式版本控制系统出现了。它可以方便的进行**分支管理**，将不同的开发内容一键合并。也可以让开发者看到项目的每一条分支的**提交记录**，以获知自己和主分支之间是否存在进度差异；它可以进行强大的**版本管理**，当开发者发现由于自己的失误导致项目出现了难以弥补的恶性 bug，或者是文件管理出现重大事故，git 支持开发者以 commit 为“锚点”进行**版本回退**，解决旧版本中的隐患或者丢掉新版本的失误；它可以提供图形化的**冲突页面**，以方便开发者了解自己修改的文件和希望合并、拉取的分支中对应的文件在哪里出现了有待商榷的差异……总之，多人协作的任何代码项目，都离不开以 git 为代表的分布式版本控制系统。而即将陪伴我们数个学期的软件工程课程，其项目也将建立在 git 之上。

{{< details title="分布式版本控制系统" >}}
在分布式版本控制系统中，系统保存的不是文件变化的差量，而是文件的快照，即把文件的整体复制下来保存，而不关心具体的变化内容。其次，最重要的是该控制系统是分布式的，开发者从中央服务器拷贝下来代码时，拷贝的是一个完整的版本库，包括历史纪录，提交记录等，这样即使某一台机器宕机也能找到文件的完整备份。

![分布式版本控制系统](/SE-Labs/images/lab1/distributed.png)
{{< /details >}}

## Git 安装

{{< tabs "uniqueid" >}}
{{< tab "Windows" >}}
安装包下载地址：<a href="https://gitforwindows.org/" target="_blank">https://gitforwindows.org/</a>

官网慢，可以用国内的镜像：<a href="https://npm.taobao.org/mirrors/git-for-windows/" target="_blank">https://npm.taobao.org/mirrors/git-for-windows/</a>

完成安装之后，就可以在 cmd 或 powershell 等命令行工具使用 git 工具了。一般情况下，在某个文件夹点击右键，你可以看到 Git Bash Here，通过这个也可以打开 Git 工具。
{{< /tab >}}
{{< tab "MacOS" >}}
在 Mac 平台上安装 Git 最容易的当属使用图形化的 Git 安装工具。

下载地址为：<a href="http://sourceforge.net/projects/git-osx-installer/" target="_blank">http://sourceforge.net/projects/git-osx-installer/</a>
{{< /tab >}}
{{< tab "Linux" >}}
尝试在终端输入 `git`，看看系统有没有安装；没有的话输入以下命令安装：
```shell
sudo apt-get install git
```
{{< /tab >}}
{{< /tabs >}}

## Git 配置

Git 提供了一个叫做 git config 的工具，用于配置或读取相应的工作环境变量。这些环境变量决定了 Git 在各个环节的管理员信息和使用方式，存放于 /etc/gitconfig (所有用户生效 –system) 或 ~/.gitconfig (当前用户配置 –global)。

需要设置一下用户信息才能使用 Git 提交 commit，在终端输入：

```shell
git config --global user.name "yourname"
git config --global user.email "youremail"
```

## Git 基本流程

### 创建仓库

首先在 Github/Gitee 平台创建仓库 (New a repositry)，克隆到本地：

```shell
git clone <remote_url> [local_dir_name]
```

或者在本地初始化仓库，并添加远程仓库链接：

```shell
git init    # 初始化仓库
git remote add origin <remote_url>  # 添加远程仓库，并命名为 origin（默认）
```

{{< hint warning >}}
如果采用 clone 的方式，一定要 `cd` 进入到克隆下来的文件夹里，才能执行后续 Git 操作
{{< /hint >}}

### 修改提交

```shell
git add <file_name>         # 将指定文件加入暂存区
git add .                   # 或使用.将项目所有文件加入暂存区（除.gitignore指定的文件外）
git commit -m "<message>"   # 将暂存区内容打包成commit，提交到本地仓库
git push                    # 将本地仓库内容提交到远程仓库
```

这样就实现了一次修改的提交和推送。

### 工作区、暂存区和本地仓库

- 工作区：即当前进行工作的文件目录，文件修改但未提交，处于已修改状态（modified）

- 暂存区：运行git add命令后文件保存的区域，也就是下次提交要保存的文件，文件处于已暂存状态（staged）

- 本地仓库：即版本库，记录了提交的完整状态和内容，该区域文件处于已提交状态（committed）或者 **相对于版本库未更改** 状态（unmodified）

![分布式版本控制系统](/SE-Labs/images/lab1/git.png)

这里简单谈一下和 **操作系统课程指导书** 的描述的分歧。操作系统课程中对于 Git 下文件的状态分为了 Untracked、Unmodified、Modified 和 Staged，其中后三者和我们这里提及的是完全一致的。

{{< details title="我们这里删去了 Untracked 这个文件状态的介绍，想想看是为什么？" >}}

显然，Untracked 这个文件状态在一个 **经过 git 初始化环境** 的项目下几乎是不可能出现的。每一个新建/删除的文件都会被 git 视为和上一个版本的不同，并且对于新建文件进行的任意更改也会直接被 `git add` 加入暂存区。事实上，不去特意解除 git 管理，只有删去的文件才能匹配到 Untracked 这个状态——但是我们为什么要管一个已经删去的文件呢？

{{< /details >}}

### 同步远程仓库

在多人合作开发的情况下，需要定期 pull 仓库保持进度同步：

```shell
git pull [<remote_name> <remote_branch>[:<local_branch>]]
```

建议同学们在每次开始工作前，先去看看 dev 分支上是否存在自己尚未拉取的commit，以便收容其他成员对于项目的开发内容，并及时解决存在的冲突。

### 分支工作

在项目开发中，常常会建立两个分支：

- master/main：存储生产环境，可部署版本
- dev：存储开发环境

当然，在多人开发中，也会为每个人建立分支，大家在各自分支上完成自己的开发任务。

这里之所以要在 master/main 之外新建一个 dev 作为开发环境，是因为我们希望 **在 master/main 分支上的内容是可以顺利部署并且稳定运行的版本**，这也就意味着我们要在 dev 分支上去解决一切出现的问题（如版本冲突、依赖兼容性）。同时，如果 dev 分支上发生了难以挽回的重大事故，我们依然保留有 master/main 这个稳定的 “旧版本” 作为版本回退的依据，而不至于放弃整个项目。

```shell
git branch -l                   # 查看所有分支
git checkout <branch_name>      # 切换到指定分支
git checkout -b <branch_name>   # 根据当前分支，新建一个分支并切换到该分支上
git merge [<branch1>] <branch2> # 将branch2合并到branch1，省略branch1参数时表示合并到当前分支
```

当合并分支出现冲突时，也就是两个人分别在各自分支上修改了同一处，Git 无法自动合并，则会报错冲突。此时需要手动修改冲突文件，可选择保留哪一分支的内容，之后再 `add/commit/push`。这里推荐在 VS Code 中进行冲突合并，同学们在完成 lab 的任务中也会感受到这一过程。

### 错误回退

Git 多工作区和版本库机制，允许你回头是岸。

如果发现提交了错误文件：

- 若文件未添加至暂存区：使用 `git checkout <filename>` 将文件替换成暂存区版本，或 `git checkout .` 将工作区内的所有文件替换成暂存区内的文件（谨慎使用）
- 若文件已添加到暂存区但未提交到本地仓库：使用 `git reset HEAD .` 撤销暂存区的所有修改至工作区，接下来就回到了上一步
- 若已提交到本地仓库：使用 `git reset --hard HRAD^` 将所有文件回退至上一版本

可以使用 `git log` 命令打印当前分支的提交记录，以选择合适的 “锚点” 进行回退。

{{< hint info >}}
本文仅介绍 Git 工作流程，具体指令见 [Git 指令全集](/SE-Labs/docs/labs/lab01/git_command/)
{{< /hint >}}

### 工具推荐

我们可以利用 Git 丰富的指令来完成版本控制和分支管理，但是可能有一些同学并不适应面对命令行的方式，实际上，在现阶段我们自己的项目的体量和技术水平下，往往并不需要进行版本回溯这种操作，一些分支合并、提交、冲突处理就基本够用了，这样简单的操作如果还要不断地写命令行未免有些繁琐。

Git 官方推出了一款面向 Windows 用户（支持mac）的 Git 图形化管理工具 [GitHub Desktop](https://desktop.github.com/)。利用这款软件，我们可以以GUI的形式完成之前CLI中绝大多数的 Git 命令，并且更加便捷。比如：

可以直接在 GitHub 上 使用 GitHub Desktop 将 **项目一键克隆到本地**，而不是还要使用 `git clone + <冗长的链接>`（如果是配置 ssh 连接的话就更麻烦了），并且可以图形化监视克隆进度，操作便捷可靠。

![GitHub Desktop 克隆项目](/SE-Labs/images/lab1/git_desktop_clone.png)

可以在工具栏的 branch 中管理自己当前项目的分支，无论是 **新建/删除分支** 还是 **进行分支合并** 都非常方便。

![GitHub Desktop 分支管理](/SE-Labs/images/lab1/git_desktop_branch.png)

对于最常见的代码提交，也可以一目了然地看到自己的更改，并写上 commit 信息以及更加具体的 description。

![GitHub Desktop 提交管理](/SE-Labs/images/lab1/git_desktop_commit.png)

GitHub Desktop 还有更多的功能（比如说上面提到的冲突管理），这里就不展开介绍了。