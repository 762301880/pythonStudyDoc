# 说明&资料

- 说明

> Django 是一个由 Python 编写的一个开放源代码的 Web 应用框架。
>
> 使用 Django，只要很少的代码，Python 的程序开发人员就可以轻松地完成一个正式网站所需要的大部分内容，并进一步开发出全功能的 Web 服务 Django 本身基于 MVC 模型，即 Model（模型）+ View（视图）+ Controller（控制器）设计模式，MVC 模式使后续对程序的修改和扩展简化，并且使程序某一部分的重复利用成为可能。

- 资料

| 名称             | 地址                                                         |
| ---------------- | ------------------------------------------------------------ |
| 菜鸟教程`django` | [链接](https://www.runoob.com/django/django-tutorial.html)   |
| 官方手册         | [链接](https://docs.djangoproject.com/zh-hans/2.1/intro/tutorial01/) |

# 二、安装`django`

## 2.1 命令下载django（默认下载的是最新版本的）

```shell
pip install django
```

## 2.2 安装成功后如何创建djago项目

- cd 进入你放置django项目的目录输入一下命令

```shell
django-admin startproject 你的项目名称=>例子：django-admin startproject HelloWorld
```

## 2.3 查看`Django `版本

```python
python -m django --version
```

## 2.4 创建完成后我们可以查看下项目的目录结构：

```api
$ cd HelloWorld/
$ tree
.
|-- HelloWorld
|   |-- __init__.py
|   |-- asgi.py
|   |-- settings.py
|   |-- urls.py
|   `-- wsgi.py
`-- manage.py
```

### 2.4.1目录说明

```python
HelloWorld: #项目的容器。
manage.py:  #一个实用的命令行工具，可让你以各种方式与该 Django 项目进行交互。
HelloWorld/__init__.py: #一个空文件，告诉 Python 该目录是一个 Python 包。
HelloWorld/asgi.py: 一个 #ASGI 兼容的 Web 服务器的入口，以便运行你的项目。
HelloWorld/settings.py: #该 Django 项目的设置/配置。
HelloWorld/urls.py: #该 Django 项目的 URL 声明; 一份由 Django 驱动的网站"目录"。
HelloWorld/wsgi.py: #一个 WSGI 兼容的 Web 服务器的入口，以便运行你的项目。
```

## 2.5 接下来我们进入 项目目录输入以下命令，启动服务器：

```python
python manage.py runserver
```

- 你应该会看到如下输出

```python
Performing system checks...

System check identified no issues (0 silenced).

You have unapplied migrations; your app may not work properly until they are applied.
Run 'python manage.py migrate' to apply them.

三月 30, 2019 - 15:50:53
Django version 2.1, using settings 'mysite.settings'
Starting development server at http://127.0.0.1:8000/   #http://127.0.0.1:8000/ 浏览器打开此服务即可
Quit the server with CONTROL-C.
```



