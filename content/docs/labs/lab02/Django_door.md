---
title: 'Django入门篇'
weight: 2004
---

# Django 入门篇

{{< hint info >}}
后端的主要功能是，管理数据库、响应前端的请求。例如用户登录，前端需要携带用户名和密码等信息向后端**某个路由**发送请求，后端则根据用户名查找**数据库**，验证密码是否正确，并携带结果**响应**前端。
{{< /hint >}}

<a href="https://www.djangoproject.com/" target="_blank">Django</a> 是一个由 Python 编写的高级 Web 框架，使用框架进行 Web 开发，能避免重复造轮子，而专注于应用程序的业务逻辑。

## 环境配置

相比于直接安装 Python 某个版本，更推荐安装 <a href="https://www.anaconda.com/" target="_blank">Anaconda</a> 管理虚拟环境。Python 项目的版本和依赖各有千秋，而使用 Anaconda 能针对项目建立虚拟环境，互不干扰且便于管理。

Anaconda下载地址：
- 官网：<a href="https://www.anaconda.com/" target="_blank">https://www.anaconda.com/</a>
- 清华镜像：<a href="https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/" target="_blank">https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/</a>（选择最新版本即可）

{{< hint warning >}}
安装步骤中注意勾选添加至环境变量中
{{< /hint >}}

安装 Anaconda 后，使用 conda 指令新建一个虚拟环境，用于开发 Django 项目：

```shell
conda create --name django python=3.8   # 虚拟环境名为django，python版本指定3.8
```

进入 django 虚拟环境：

```shell
conda activate django
```

{{< details title="Conda常用指令" >}}
```shell
conda info --env        # 查看所有虚拟环境
conda create --name <name> python=<version> # 新建环境
conda activate <name>   # 进入虚拟环境
conda deactivate        # 退出环境
```
{{< /details >}}

安装 django 依赖：

```shell
pip install django
```

当然，如果你不安装 Anaconda，也可以直接通过上面最后一条指令安装 django 依赖。

## 新建项目

{{< tabs "django_init" >}}
{{< tab "命令行创建" >}}
在某个文件夹内打开终端，输入下面指令创建 Django 项目：

```shell
django-admin startproject press # 新建名为 press（出版社）的项目
```

创建成功后，出现了 `press` 文件夹，在目录下可以看到 `press` 文件夹和 `manage.py` 文件，其内容主要是项目运行入口和总配置，接下来我们先创建一个 app（应用程序），用于实现业务逻辑，包含数据库模型的建立、建立路由和API响应前端的请求。

```shell
python manage.py startapp publish   # 新建名为 publish 的 app
```

创建 app 成功后，目录下多出一个文件夹名为 `publish`，包含 views、models 等文件。先不管项目内容，输入以下命令，让项目跑起来：

```shell
python manage.py runserver
```

运行成功后，将提示运行在 <a href="http://127.0.0.1:8000/" target="_blank">http://127.0.0.1:8000/</a>，浏览器打开即可。
{{< /tab >}}
{{< tab "Pycharm创建" >}}
用Pycharm新建项目十分方便，省去了命令行操作，点击导航栏文件处，选择新建项目。

如下图，如果已新建好 Conda 虚拟环境，请配置已有环境。此处我还选择了新建名为 `publish` 的 app，将在该 app 中实现业务逻辑，包含数据库模型的建立、建立路由和API响应前端的请求。

![pycharm新建项目](/SE-Labs/images/lab2/pycharm.png)

新建成功后，点击右上角运行按钮。运行成功后，将提示运行在 <a href="http://127.0.0.1:8000/" target="_blank">http://127.0.0.1:8000/</a>，浏览器打开即可。
{{< /tab >}}
{{< /tabs >}}

## 了解项目结构

经过上述步骤，我们创建了 django 项目，在新建了名为 `publish` 的 app。

目录结构如下：

```shell
press
|-- publish             # app目录
|   |-- __init__.py     # python包声明
|   |-- admin.py
|   |-- apps.py         # app配置文件
|   |-- models.py       # 数据库模型配置
|   |-- tests.py        # 测试模块
|   `-- views.py        # 视图编写文件（API-实现业务逻辑，响应前端的请求）
|-- press
|   |-- __init__.py
|   |-- asgi.py
|   |-- settings.py     # 项目配置文件
|   |-- urls.py         # 后端路由设置
|   `-- wsgi.py         # uwsgi运行入口
|-- manage.py           # django命令行工具
`-- db.sqlite3          # 数据库文件
```

看到这里有可能有点模糊，拎几个重点的需要修改的文件出来介绍：

- publish/models.py：数据库模型设置，在这里要建立数据库表项及其属性
- publish/views.py：编写api的文件，在这里要编写和规划所有的请求处理函数。
- press/settings.py：项目总配置文件，在这里实现跨域设置、app信息等
- press/urls.py：后端路由设置，在这里指定后端API的路由，以供前端发送请求

## 项目预设置

### 添加 APP 信息

若是在 Pycharm 中创建的项目，在 press/settings.py 中已自动添加好 app 信息，无需再度添加；如果是命令行创建，则需在 settings 文件的 `INSTALLED_APPS` 中添加 app 名字：

```python
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'publish',  # app name
]
```

在这里添加 app 的名字，是为了告诉 django 这个 python 包是这个项目的一个 app。

### 路由分发

一个较大的项目可能需要建立多个app，在其中实现业务逻辑，这样不同 app 全部 api 的路由都在一个文件中（press/urls.py）添加是不合适的。因此，可以在各 app 下新建 urls.py 文件，并在总的路由文件中指定包含这些文件。具体操作请看下面：

首先，在 app（publish目录） 下新建 `urls.py` 文件，内容如下：

```python
# publish/urls.py
from django.urls import path
from .views import *

urlpatterns = [
    # path('url_name', api_name)
    # 这是一个样例，指定路由名为url_name，对应处理函数为当前app内views.py中的api_name
]
```

接着在项目配置目录（press目录）的 `urls.py` 引入上面文件的路由：

```python
# press/urls.py
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('api/admin/', admin.site.urls),
    path('api/publish/', include(('publish.urls', 'publish'))),
    # 将各app（如publish）中指定的路由导入到总路由中
]
```

上述操作实现了将 publish 这个 app 指定的 urls，全部接到了路由 `api/publish/` 之后。

## 示例 出版网站

假设要开发一个出版网站，最基本的是给作者提供注册、登录和退出登录这三个功能。

> 假设作者的用户名唯一，可作为用户标识

逻辑：

- 当前端发来注册请求时，后端验证两次密码是否一致，成功后将信息填入到数据库中；
- 当前端发来登录请求时，后端需要拿着用户名到数据库中查询，验证密码是否正确，再返回给前端信息；若登录成功还需存储登录信息；
- 当前端发来退出登录请求时，后端需要清空登录信息，并返回结果。

### 数据库模型

完成上述逻辑前，我们需要先修改 `publish/models.py`，添加 `author` 用户的表项。

```python
# publish/models.py
from django.db import models

class Author(models.Model):
    # Author表项，含用户名和密码，均为字符串属性，并设置最大长度
    username = models.CharField(max_length=100)
    password = models.CharField(max_length=20)
```

在修改数据库模型之后，**一定要**生成迁移文件，并应用新的数据库模型。在终端输入以下命令实现：

```shell
python manage.py makemigrations # 生成迁移文件
python manage.py migrate        # 迁移数据库模型
```

> 输入上述命令迁移后运行，可以发现在项目根目录出现了 `db.sqlite3` 文件。这是一个数据库文件，如何可视化请见后面[sqlite 数据库可视化](/SE-Labs/docs/labs/lab02/django_door/#sqlite-数据库可视化)，你也可以先看可视化部分再回头。

{{< details title="数据库模型指令介绍" >}}

#### Django 的 Model 数据类型

| 数据类型 | 说明 |
| - | - |
| AutoField | 根据 ID 自增长的 IntegerField 字段，通常用于主键ID |
| IntegerField | 32位整数，可自定义选项 |
| BooleanField | 布尔值(True/False)字段 |
| CharField | 字符串字段，对小字符串和大字符串都适用；对于大量文本建议使用TextField。必须参数：max_length（字段的最大字符数）|
| DateField | 利用 Python 的 datetime.date 实例来表示日期 |
| DateTimeField | 利用 datetime.datetime 实例表示日期和时间 |
| EmailField | 带有 email 合法性检测的CharField，默认max_length=75 |
| TextField | 超大文本字段 |
| FileField | 文件字段 |
| ImageField | 继承于FileField，确保是有效图片 |

#### Model 数据类型的通用参数

| 参数 | 说明 |
| - | - |
| null | 是否允许为空值，默认为false |
| default | 该属性的默认值 |
| primary_key | 该属性是否为主键，默认为false |
| unique | 该属性的值是否唯一，默认为false |

#### 时间类型的可选参数

- DateField.auto_now：设为 `True` 时，每一次保存对象时，Django 都会自动将该字段的值设置为当前时间。一般用来表示最后修改时间。
- DateField.auto_now_add：设为 `True` 时，第一次创建对象时，Django 自动将该字段的值设置为当前时间，一般用来表示对象创建时间。
{{< /details >}}

### 注册功能

完成一个业务功能的实现，一般分为两步：编写业务逻辑处理函数，指定路由。

先实现业务逻辑，在 `publish/views.py` 中编写 API 函数，内容如下：

```python
# publish/views.py
from django.http import JsonResponse
from django.views.decorators.csrf import csrf_exempt
from publish.models import Author   # 引入数据库 Author 对象

@csrf_exempt    # 跨域设置
def register(request):  # 继承请求类
    if request.method == 'POST':  # 判断请求方式是否为 POST（此处要求为POST方式）
        username = request.POST.get('username')  # 获取请求体中的请求数据
        password_1 = request.POST.get('password_1')
        password_2 = request.POST.get('password_2')
        if password_1 != password_2:    # 若两次输入的密码不同，则返回错误码errno和描述信息msg
            return JsonResponse({'errno': 1002, 'msg': "两次输入的密码不同"})
        else:
            # 新建 Author 对象，赋值用户名和密码并保存
            new_author = Author(username=username, password=password_1)
            new_author.save()   # 一定要save才能保存到数据库中
            return JsonResponse({'errno': 0, 'msg': "注册成功"})
    else:
        return JsonResponse({'errno': 1001, 'msg': "请求方式错误"})
```

{{< hint info >}}
HTTP八大请求详情可见[HTTP八大请求](/SE-Labs/docs/else/res/httprequest/)，常用GET和POST。
- GET：用于获取资源，请求中不应该包含数据体。
- POST：用于提交数据，数据被包含在请求体中，处理该请求服务器可能会建立或更新资源。
{{< /hint >}}

{{< details title="Django数据库存取操作" >}}
#### 增

```python
# 方法一
user = User()
user.name = "ZewanHuang"
user.save()
# 方法二
user = User(id=1, name="ZewanHuang")
user.save()
# 方法三
User.objects.create(id=1, name="ZewanHuang")
```

#### 查

```python
# 查询特定结果
user = User.objects.get(id=1)
# 查看多个结果（返回一个列表）
users = User.objects.filter(kind=‘学生’)
# 查询全部结果
users = User.objects.all()
```

#### 改

```python
# 方法一：查后改后保存
user = User.objects.get(id=1)
user.name = "Zewan"
user.save()
# 方法二：更新
users = User.objects.filter(kind="学生")
users.update(kind="老师")
```

#### 删

```python
user = User.objects.get(id=1)
user.delete()
```
{{< /details >}}

接下来为该 API 指定路由，在 `publish/urls.py` 中添加：

```python
# publish/urls.py
from django.urls import path
from .views import *

urlpatterns = [
    path('register', register),  # 指定register函数的路由为register
]
```

由于前面做了路由的 `include` 设置，因此该 register 对应的路由为 `api/publish/register`，若项目运行在 8000 端口，则完整的路由为 <a href="http://127.0.0.1:8000/api/publish/register" target="_blank">http://127.0.0.1:8000/api/publish/register</a>。

这样实现后，该 API 详细信息为：

- 路由：http://127.0.0.1:8000/api/publish/register
- 请求数据：用户名 `username`，密码 `password_1`，确认密码 `password_2`
- 响应数据：JSON格式，错误码 `errno` 和描述信息 `msg`
- 响应样例：
    ```json
    {
        "errno": 0,
        "msg": "注册成功"
    }
    ```

> 如何测试API在后面[Postman测试](/SE-Labs/docs/labs/lab02/django_door/#postman-测试)中介绍，你也可以先看测试部分再回头

### 登录功能

理解注册API后，登录也是一样的套路。

请求处理函数：

```python
# publish/views.py
@csrf_exempt
def login(request):
    if request.method == 'POST':
        username = request.POST.get('username')  # 获取请求数据
        password = request.POST.get('password')
        author = Author.objects.get(username=username)
        if author.password == password:  # 判断请求的密码是否与数据库存储的密码相同
            # 密码正确则将用户名存储于session（django用于存储登录信息的数据库位置）
            request.session['username'] = username
            return JsonResponse({'errno': 0, 'msg': "登录成功"})
        else:
            return JsonResponse({'errno': 1002, 'msg': "密码错误"})
    else:
        return JsonResponse({'errno': 1001, 'msg': "请求方式错误"})
```

{{< details title="Django session 存储登录信息" >}}
**session**：临时保存在服务器端的用户数据，本质是键值对。将用户登录时的ID（标志）存储在 session 中以便后续获取，当处理修改用户信息等请求时，从中获取并核验身份，防止用户能修改其它用户的信息

登录时：
```python
# 如果登录成功，存储用户标志信息
if user.password == password: 
    request.session['id'] = user.id
	request.session['kind'] = "user"
```

检查登录信息时，需要获取 session 存储的数据：
```python
username = request.POST.get('username')
if request.session.get('username') == username:
    # 若session存储数据和请求的用户名相同，则登录信息核验成功
    # 防止用户能修改其它用户的信息
```
{{< /details >}}

添加路由：

```python
# publish/urls.py
urlpatterns = [
    path('register', register),  # 指定register函数的路由为register
    path('login', login)
]
```

### 退出登录功能

处理函数：

```python
@csrf_exempt
def logout(request):
    request.session.flush()
    return JsonResponse({'errno': 0, 'msg': "注销成功"})
```

指定路由：

```python
urlpatterns = [
    path('register', register),  # 指定register函数的路由为register
    path('login', login),
    path('logout', logout)
]
```

## sqlite 数据库可视化

这里只展示 Pycharm 如何可视化 `db.sqlite3` 文件。

在 Pycharm 右侧侧边栏处，点击 Database 按钮，添加 Data Source：

![sqlite1](/SE-Labs/images/lab2/sqlite1.png)

在弹出的选项框中，选择项目根目录的 sqlite3 文件；若提示缺失驱动，点击下载并测试连接，成功后点击确认即可：

![sqlite2](/SE-Labs/images/lab2/sqlite2.png)

若未显示数据库，请按下图操作：

![sqlite3](/SE-Labs/images/lab2/sqlite3.png)

## Postman 测试

前后端分离开发中，仅后端一般无法通过点击图形化界面进行测试，后端的测试也不应该依赖于前端，而应该独立进行。因此后端的测试，需要借助工具模拟前端请求，向后端相应的路由发送请求，并查看响应数据。

<a href="https://www.postman.com/" target="_blank">Postman</a> 就是这样的工具。

Postman 下载地址：<a href="https://www.postman.com/" target="_blank">https://www.postman.com/</a>

注册账号，下载后登录 Postman，点击客户端左上角 Workspaces 组件，可为你的项目创建一个工作区，如果你对保存请求信息不感冒，使用默认 My Workspace 也可以。Postman 仅仅是测试的工具，因此这里也不多介绍管理文件夹存储请求记录这些东西了。

下面示例测试注册接口：

![postman](/SE-Labs/images/lab2/postman.png)

可以看到返回数据是 JSON 格式，且提示注册成功。

## 简单的调试方法

对后端来说，如果使用 Postman 发送请求后结果和预料的正常结果不一致，但这时候我们只知道哪个函数出错了，难以缩小 bug 的范围并找出原因。

这里提供一个非常简单的小技巧，可以在 Python 出错的函数中，加上一些 `print` 输出，然后用 Postman 再次发请求，你可以在跑后端的终端中查看到你 print 的信息。

举个非常简单的例子，现在我查询文章列表出 bug 了，我想判断有没有进入循环，就可以在 `for` 循环内加入 `print(1)`，然后用 Postman 再发一次请求，就能在跑后端的终端中看是否有 `1` 输出，没有则未进入循环。（万能的 `print` 法找 bug）