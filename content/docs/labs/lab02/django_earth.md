---
title: 'Django入土篇'
weight: 2005
---

# Django 入土篇

## Django 从入门到入土

Liujiang Blog：https://www.liujiangblog.com/course/django/84

{{< button href="https://www.liujiangblog.com/course/django/84" >}}Get Liujiang Blog{{< /button >}}

Marvolo Djangobook（强力推荐，必须得看！19级dalao专门写的教程，里面教了如何购买云服务器，云数据库，使用 Datagrip 等进阶知识）：https://super-buaa-2021.github.io/Djangobook/

{{< button href="https://super-buaa-2021.github.io/Djangobook/" >}}Get Djangobook{{< /button >}}

Bilibili Video（强力推荐，如果有时间可以看一看，看到 P79集，足以出色的完成软工一，小学期）：https://www.bilibili.com/video/BV1b5411c7Sa/

{{< button href="https://www.bilibili.com/video/BV1b5411c7Sa/" >}}Get Bilibili Video{{< /button >}}



## Django 指令或代码指示

### 项目指令

```shell
django-admin startproject <project_name>    # 创建项目
python manage.py startapp <app_name>        # 创建APP
python manage.py runserver                  # 本地运行
python manage.py makemigrations             # 生成迁移文件
python manage.py migrate                    # 迁移数据库模型
```

### Django Models

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

### Django 数据库增删查改

我们以下面这个这个类举例

```python
class Book(models.Model):
	title = models.CharField('书名', max_length=50, default='')
    price = models.DecimalField('定价', max_digits=7, decimal_places=2,default=0.0)
	author = models.CharField('作者姓名',max_length=50,default='')
```

#### 增

```python
# 方法一
book = Book()
book.title = "软件工程基础指导"
book.author = "吕云翔"
user.save()
# 方法二
book = Book(id=1, title="软件工程基础指导", author="吕云翔")
book.save()
# 方法三
book = Book.objects.create(id=1, title="软件工程基础指导", author="吕云翔")
```

#### 查

```python
# 查询特定结果（返回一个类的对象）
book = Book.objects.get(id=1)	# 查询 id 为 1 的书
# 查询全部结果（返回一个QuerySet）
books = Book.objects.all()		# 返回数据库所有书
# 筛选多个结果（返回一个QuerySet，不是list，可以通过列表表达式转换成一个列表）
books = Book.objects.filter(author="吕云翔")  # 查询所有吕云翔老师编写的书
books = Book.objects.exclude(author="吕云翔")  # 查询除吕云翔老师编写之外的书

# 进行非等值查询（返回一个QuerySet）
1. 模糊查询 __contains
Book.objects.filter(author__contains='吕') # 查询姓吕的作者编写的书
2. 大小关系 __gt __gte __lt __lte
Book.objects.filter(price__gt=30.0, author__contains='吕') # 查询售价大于30元的，且是姓吕的作者编写的书 (filter中由多个查询条件为'与'的关系)
3. 存在关系 __in
Book.objects.filter(author__in = ['吕云翔','周恩申'，'李昊'，'闫思桥']) 
4. 范围 __range
Book.objects.filter(id__range=(35,50))

对于QuerySet类型，我们可以进行多次查询操作
Book.objects.filter(price__gt=30.0, author__contains='吕').exclude(author="吕云翔")
```

同样的，ORM也支持聚合查询（数据库课程中也会提到），Django 可以采用聚合函数来进行聚合查询，其内部的实现方式也是基于上述介绍的过滤器等查询方法。

#### 改

```python
# 方法一：查后改后保存
book = Book.objects.get(id=1)
book.author = "周恩申"
book.save()
# 方法二：更新
books = Book.objects.filter(author="吕云翔")
books.update(author="周恩申")
```

#### 删

```python
book = Book.objects.get(id=1)
book.delete()
```

