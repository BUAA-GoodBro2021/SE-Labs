---
title: 'Lab01 Git'
weight: 100
---

# Lab01 Git

## 实验目的

- 了解分布式版本控制系统的概念
- 掌握 Git 的基本指令
- 实践团队如何使用 Git 进行合作开发
- 实践分支合并时冲突的解决

## 资源链接

<a href="https://bhpan.buaa.edu.cn:443/link/2B8C3DF0CE32D21908D8007C843940A5" target="_blank">https://bhpan.buaa.edu.cn:443/link/2B8C3DF0CE32D21908D8007C843940A5</a>

Valid Until: 2022-08-01 23:59

## 实验指南

1. 观看上述云盘链接中 Lab01 的视频
2. 文字教程可查阅[Git简易教程](/SE-Labs/docs/labs/lab01/git/) 和[Git指令全集](/SE-Labs/docs/labs/lab01/git_command/)
3. 完成实验作业并于 3.20 日晚 12 点前提交至 <a href="https://scs.buaa.edu.cn/" target="_blank">软院云平台</a>

## 实验作业

{{< hint info >}}
远程仓库可选 Gitee 或 Github；操作过程中请保存好截图，根据后面所讲的提交方式打包提交。
{{< /hint >}}

### 任务一 个人作业

1. 远程仓库上新建代码仓库（private），仓库名：Platform-学号。
    
    <span style="color: red">**在仓库主页截图**</span>

2. 远程仓库上以 master/main 分支为基础，新建 dev 分支，添加 `index.html` 文件。（master/main 分支存储生产环境，dev 分支存储开发环境）
    
    <span style="color: red">**在dev分支主页截图**</span>

3. clone 远程仓库到本地，创建本地 dev 分支与远程同步。（此处结果应为在本地 dev 分支看到 `index.html` 文件）
    
    <span style="color: red">**在控制台和本地目录截图**</span>

4. 在本地修改 `index.html` 文件（内容如下），上传本地改动到远程仓库。
    
    <span style="color: red">**控制台命令、仓库主页查看 index.html 截图**</span>
    {{< details title="index.html 文件修改内容" >}}
    <!DOCTYPE html>
    <head>
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width,initial-scale=1.0,user-scalable=no,viewport-fit=cover">
        <meta name="keywords" content="北航软件工程基础">
        <title>Lab01 任务一</title>
    </head>
    <body>
        <h1>Lab01 任务一</h1>
    </body>
    </html>
    {{< /details >}}
5. 在远程修改 `index.html` 文件（内容如下），本地同步远程改动。

    <span style="color: red">**本地查看 index.html 内容截图**</span>
    {{< details title="index.html 文件修改内容" >}}
    <!DOCTYPE html>
    <head>
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width,initial-scale=1.0,user-scalable=no,viewport-fit=cover">
        <meta name="keywords" content="北航软件工程基础">
        <title>Lab01 任务一</title>
    </head>
    <body>
        <h1>Lab01 任务一</h1>
        <h2>姓名</h2>
    </body>
    </html>
    {{< /details >}}
6. 在本地合并 dev 分支到 master/main 分支，提交本地改动到远程仓库，并在远程 master/main 查看 `index.html` 内容。（以上结果是本地和远程的 master、dev 分支都可以看到 `index.html` 的最新改动）
    
    <span style="color: red">**在网页 master/main 分支查看 index.html 内容并截图**</span>


### 任务二 小组作业

{{< hint warning >}}
请保留任务二所创建的仓库一周；

任务二小组共同完成一份文档，文档模板见所给云盘资源 Lab01。
{{< /hint >}}

#### 初始创建与同步

1. 组长在远程仓库上新建 public 代码仓库，仓库名：Study-组号，并为组员授权。

    <span style="color: red">**仓库主页截图、仓库授权用户截图**</span>

2. 远程仓库上以 master/main 分支为基础，创建 dev 分支，添加 `main.py` 文件。

3. 各小组成员 clone 远程仓库到本地，创建本地 dev 分支与远程同步。

#### 合并分支练习

4. 组长在远程仓库以 dev 分支为基础，为各个组员（包括自己）创建 `exercise-学号` 分支，各组员创建本地 `exercise-学号` 分支，同步远程代码仓库，在本地 `exercise-学号` 分支添加 `function_学号.py` 文件（各组员在自己的分支修改），上传本地改动至远程仓库。

    <span style="color: red">**各组员本地 Git 命令行截图和远程仓库各分支文件内容截图**</span>

    {{< details title="`function_学号.py` 文件修改内容" >}}
    print('My student_id: 学号')
    {{< /details >}}

5. 各组员在本地将 `exercise-学号` 合并到 dev 分支。

6. 上传到远程仓库 dev 分支。

    <span style="color: red">**远程仓库 dev 分支截图**</span>

#### 合并分支冲突

7. 各组员同步远程 dev 分支更新，确保此时内容为最新内容。

8. 各组员修改本地 `exercise-学号` 分支的 `main.py` 文件。

    {{< details title="`main.py` 文件修改内容" >}}
    import os
    os.system('python function_学号.py')
    {{< /details >}}

9. 各组员在本地将 `exercise-学号` 分支合并到 dev 分支。

    <span style="color: red">**各组员 Git 命令截图**</span>

10. **等所有组员结束上一步骤后，先组长再组员**依次上传到远程 dev 分支，冲突时一律保留组长的修改。（解决冲突执行 commit 时注明信息为 `conflict solved`）

    <span style="color: red">**各组员 Git 命令截图和处理冲突截图**</span>

{{< hint info >}}
执行第10步骤时，当其他人 push 后你无法直接 push（当然你可以先尝试 push 看有无警告），需要 pull 同步他人修改后才能 push，而此时 pull 下来后你就会发现有冲突了
{{< /hint >}}

#### 完成发布

11. 待第10步骤完成后，组长在本地同步仓库 dev 分支，合并到 master/main 分支，并上传到远程 master/main 分支。

    <span style="color: red">**组长 Git 命令截图和仓库主页 master/main 分支的 `main.py` 文件内容**</span>


### 提交方式

- 截止时间：**2022/3/20 晚12点**
- 提交方式：<a href="https://scs.buaa.edu.cn/" target="_blank">软院云平台</a>
- 提交内容：两个 word 文档或 pdf 文档，放在压缩包内，命名格式如下

```txt
学号_姓名_第1次实验.zip
|-- 学号_姓名_第1次实验_任务1.docx/pdf
`-- 学号_姓名_第1次实验_任务2.docx/pdf
```

{{< hint warning >}}
#### 注意事项

1. 文档中必须包括各步骤说明以及相关截图。
2. commit 时要求说清楚更改的内容。
3. 任务二小组共同完成一份文档，组长和组员都需提交，文档模板见所给云盘资源 Lab01。
{{< /hint >}}