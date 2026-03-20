# 005：Django入门

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_1.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_3.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_4.png)

在本节课中，我们将学习如何使用Django框架来构建动态Web应用。我们将从理解HTTP请求与响应的基本概念开始，逐步学习如何创建Django项目和应用，定义视图和URL，使用模板渲染动态内容，处理表单数据，并利用会话（Session）来存储用户特定的信息。

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_6.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_7.png)

---

## 概述：什么是Django？

Django是一个基于Python的Web框架，它允许我们编写Python代码来动态生成HTML和CSS，从而构建功能丰富的Web应用。与静态网页不同，动态网页的内容可以根据用户交互、时间或其他数据源而变化。

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_9.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_11.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_13.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_14.png)

## HTTP请求与响应

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_16.png)

Web通信的核心是HTTP协议。当用户在浏览器中输入一个URL时，浏览器会向服务器发送一个HTTP请求。服务器处理该请求后，会返回一个HTTP响应。

一个典型的HTTP请求如下：
```http
GET / HTTP/1.1
Host: www.example.com
```

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_18.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_19.png)

一个典型的HTTP响应如下：
```http
HTTP/1.1 200 OK
Content-Type: text/html
```

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_21.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_23.png)

常见的HTTP状态码包括：
*   **200 OK**：请求成功。
*   **404 Not Found**：请求的资源不存在。
*   **301 Moved Permanently**：资源已永久重定向。
*   **403 Forbidden**：没有权限访问资源。
*   **500 Internal Server Error**：服务器内部错误。

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_25.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_26.png)

## 创建第一个Django项目

首先，我们需要安装Django并创建一个新项目。

### 安装Django
使用Python的包管理器pip进行安装：
```bash
pip3 install django
```

### 创建项目
使用`django-admin`命令创建一个名为`lecture3`的新项目：
```bash
django-admin startproject lecture3
```
此命令会生成一个包含基础配置文件的目录。

### 项目结构
进入项目目录，你会看到以下关键文件：
*   `manage.py`：用于执行项目管理命令的工具。
*   `settings.py`：项目的配置文件。
*   `urls.py`：项目的URL路由配置文件，可视为网站的“目录”。

### 运行开发服务器
在项目根目录下运行以下命令启动开发服务器：
```bash
python manage.py runserver
```
服务器启动后，在浏览器中访问 `http://127.0.0.1:8000`，你将看到Django的默认欢迎页面。

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_28.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_30.png)

## 创建Django应用

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_32.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_33.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_35.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_37.png)

一个Django项目可以包含多个应用（App）。应用是项目中实现特定功能的模块。

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_39.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_41.png)

### 创建应用
在项目目录下，运行以下命令创建一个名为`hello`的应用：
```bash
python manage.py startapp hello
```
这会在项目中创建一个`hello`目录。

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_43.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_45.png)

### 安装应用
创建应用后，需要将其添加到项目的`settings.py`文件中的`INSTALLED_APPS`列表里：
```python
INSTALLED_APPS = [
    ...
    'hello',
]
```

## 视图与URL配置

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_47.png)

视图（View）决定了用户访问某个URL时看到的内容。URL配置则将特定的URL路径映射到对应的视图函数。

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_49.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_51.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_52.png)

### 创建第一个视图
在`hello/views.py`文件中，我们定义一个简单的视图函数：
```python
from django.http import HttpResponse

def index(request):
    return HttpResponse("Hello, world!")
```

### 配置应用级URL
在`hello`目录下创建一个`urls.py`文件，并配置URL路由：
```python
from django.urls import path
from . import views

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_54.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_56.png)

urlpatterns = [
    path('', views.index, name='index'),
]
```

### 配置项目级URL
在项目的`lecture3/urls.py`文件中，将应用的URL包含进来：
```python
from django.urls import include, path

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_58.png)

urlpatterns = [
    path('hello/', include('hello.urls')),
    ...
]
```

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_60.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_62.png)

现在，访问 `http://127.0.0.1:8000/hello/`，你将看到“Hello, world!”。

## 动态URL与模板

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_64.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_65.png)

上一节我们创建了返回简单文本的视图。本节中，我们将学习如何创建动态URL以及使用模板来渲染更复杂的HTML页面。

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_67.png)

### 带参数的URL
我们可以创建能接受参数的URL模式。例如，创建一个向任何人问好的视图。

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_69.png)

首先，在`views.py`中定义`greet`函数：
```python
def greet(request, name):
    return HttpResponse(f"Hello, {name.capitalize()}!")
```

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_71.png)

然后，在`hello/urls.py`中添加一个带参数的路径：
```python
urlpatterns = [
    ...
    path('<str:name>', views.greet, name='greet'),
]
```
尖括号`<str:name>`定义了一个名为`name`的字符串参数。现在，访问`/hello/brian`会显示“Hello, Brian!”。

### 使用模板渲染HTML
将HTML代码直接写在Python字符串中很不方便。Django允许我们使用模板（Template）来分离Python逻辑和HTML展示。

首先，在`hello`应用下创建目录结构：`templates/hello/`。然后在该目录下创建`greet.html`文件：
```html
<!DOCTYPE html>
<html>
    <head>
        <title>Greetings</title>
    </head>
    <body>
        <h1>Hello, {{ name }}!</h1>
    </body>
</html>
```
双花括号`{{ name }}`用于插入变量。

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_73.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_75.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_76.png)

修改`greet`视图，使其渲染模板并传递上下文（Context）：
```python
from django.shortcuts import render

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_78.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_80.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_81.png)

def greet(request, name):
    return render(request, "hello/greet.html", {
        "name": name.capitalize()
    })
```

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_83.png)

## 模板中的逻辑控制

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_85.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_86.png)

Django的模板语言不仅支持变量替换，还支持条件判断和循环等逻辑。

### 条件语句示例：新年检查
我们创建一个新应用`newyear`，用于检查当天是否是新年（1月1日）。

创建应用并配置URL后，在`newyear/views.py`中编写视图逻辑：
```python
import datetime
from django.shortcuts import render

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_88.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_89.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_91.png)

def index(request):
    now = datetime.datetime.now()
    return render(request, "newyear/index.html", {
        "newyear": now.month == 1 and now.day == 1
    })
```

在模板`templates/newyear/index.html`中使用条件语句：
```html
<!DOCTYPE html>
<html>
    <head>
        <title>Is it New Year's?</title>
    </head>
    <body>
        {% if newyear %}
            <h1>YES</h1>
        {% else %}
            <h1>NO</h1>
        {% endif %}
    </body>
</html>
```
`{% if ... %}`和`{% endif %}`标签用于包裹条件逻辑块。

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_93.png)

### 循环语句示例：任务列表
我们再创建一个`tasks`应用来管理待办事项列表。

在`tasks/views.py`中，我们定义一个任务列表并传递给模板：
```python
from django.shortcuts import render

def index(request):
    return render(request, "tasks/index.html", {
        "tasks": ["Foo", "Bar", "Baz"]
    })
```

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_95.png)

在模板`templates/tasks/index.html`中使用循环来渲染列表：
```html
<ul>
    {% for task in tasks %}
        <li>{{ task }}</li>
    {% endfor %}
</ul>
```
`{% for ... in ... %}`和`{% endfor %}`标签用于遍历序列。

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_97.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_99.png)

## 处理表单与用户输入

一个完整的Web应用需要与用户交互。本节我们将学习如何在Django中创建和处理表单。

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_101.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_103.png)

### 创建添加任务的表单
首先，创建一个用于添加新任务的页面。在`tasks/urls.py`中添加新路径：
```python
urlpatterns = [
    path('', views.index, name='index'),
    path('add', views.add, name='add'),
]
```

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_105.png)

创建对应的视图函数和模板。在`add.html`中，我们创建一个简单的表单：
```html
<form action="{% url 'tasks:add' %}" method="post">
    {% csrf_token %}
    <input type="text" name="task">
    <input type="submit">
</form>
```
*   `action`属性指定表单提交的URL。我们使用`{% url 'tasks:add' %}`来动态生成URL，避免硬编码。
*   `method="post"`表示使用POST方法提交数据。
*   `{% csrf_token %}`是Django为防止跨站请求伪造（CSRF）攻击而要求添加的安全令牌。

### 处理POST请求
在`views.py`的`add`函数中，我们需要区分GET请求（显示空表单）和POST请求（处理表单数据）：
```python
from django.shortcuts import render, redirect
from django.urls import reverse

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_107.png)

def add(request):
    if request.method == "POST":
        # 处理表单提交
        new_task = request.POST["task"]
        # 将新任务添加到列表（这里先用全局变量模拟）
        tasks.append(new_task)
        # 重定向回任务列表页
        return redirect(reverse("tasks:index"))
    else:
        # 显示空表单
        return render(request, "tasks/add.html")
```

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_109.png)

### 使用Django表单类
手动编写HTML表单并验证数据比较繁琐。Django提供了表单类来简化这个过程。

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_111.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_113.png)

在`views.py`中导入forms并定义一个表单类：
```python
from django import forms

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_115.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_117.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_119.png)

class NewTaskForm(forms.Form):
    task = forms.CharField(label="New Task")
    priority = forms.IntegerField(label="Priority", min_value=1, max_value=5)
```

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_121.png)

在视图中使用这个表单类：
```python
def add(request):
    if request.method == "POST":
        form = NewTaskForm(request.POST)
        if form.is_valid():
            # 获取验证通过的数据
            task = form.cleaned_data["task"]
            # ... 处理任务 ...
            return redirect(reverse("tasks:index"))
        else:
            # 将包含错误信息的表单返回给用户
            return render(request, "tasks/add.html", {"form": form})
    else:
        return render(request, "tasks/add.html", {"form": NewTaskForm()})
```

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_123.png)

在模板中，可以直接渲染表单字段：
```html
<form action="{% url 'tasks:add' %}" method="post">
    {% csrf_token %}
    {{ form }}
    <input type="submit">
</form>
```
Django会自动生成HTML输入字段并实施客户端验证。

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_125.png)

## 模板继承与静态文件

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_127.png)

为了提高代码复用性和可维护性，Django支持模板继承。同时，我们还需要管理CSS、JavaScript等静态文件。

### 模板继承
许多页面有相同的结构（如页头、页脚）。我们可以创建一个基础模板（`layout.html`），让其他模板继承它。

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_129.png)

创建`templates/tasks/layout.html`：
```html
<!DOCTYPE html>
<html>
    <head>
        <title>Tasks</title>
    </head>
    <body>
        {% block body %}
        {% endblock %}
    </body>
</html>
```
`{% block body %}`定义了一个可以被子模板覆盖的区块。

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_131.png)

修改`index.html`和`add.html`，使其继承基础模板：
```html
{% extends "tasks/layout.html" %}

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_133.png)

{% block body %}
    <h1>Tasks</h1>
    <ul>
        {% for task in tasks %}
            <li>{{ task }}</li>
        {% endfor %}
    </ul>
    <a href="{% url 'tasks:add' %}">Add a New Task</a>
{% endblock %}
```

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_135.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_137.png)

### 管理静态文件
静态文件（如CSS、图片）应放在应用的`static`目录下。

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_139.png)

在`tasks`应用下创建`static/tasks/styles.css`文件并添加样式。

在模板中加载并使用静态文件：
```html
{% load static %}
<!DOCTYPE html>
<html>
    <head>
        <title>Tasks</title>
        <link rel="stylesheet" href="{% static 'tasks/styles.css' %}">
    </head>
    <body>
        ...
    </body>
</html>
```
`{% load static %}`标签用于加载静态文件标签。`{% static 'path/to/file' %}`用于生成静态文件的正确URL。

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_141.png)

## 会话（Session）与用户数据

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_143.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_144.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_146.png)

之前我们将任务列表存储在全局变量中，这导致所有用户共享同一个列表。为了解决这个问题，我们需要使用会话来为每个用户存储独立的数据。

### 使用会话存储任务列表
修改`tasks/views.py`中的`index`和`add`视图，将会话作为数据存储介质：

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_148.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_150.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_151.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_153.png)

```python
def index(request):
    # 如果会话中没有“tasks”键，则初始化一个空列表
    if "tasks" not in request.session:
        request.session["tasks"] = []
    return render(request, "tasks/index.html", {
        "tasks": request.session["tasks"]
    })

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_155.png)

def add(request):
    if request.method == "POST":
        form = NewTaskForm(request.POST)
        if form.is_valid():
            task = form.cleaned_data["task"]
            # 将任务添加到当前会话的任务列表中
            request.session["tasks"] += [task]
            return redirect(reverse("tasks:index"))
        else:
            return render(request, "tasks/add.html", {"form": form})
    else:
        return render(request, "tasks/add.html", {"form": NewTaskForm()})
```

### 启用会话支持
Django默认将会话数据存储在数据库中。首次使用前，需要创建数据库表：
```bash
python manage.py migrate
```
运行此命令会创建Django所需的所有默认数据表，包括会话表。

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_157.png)

现在，不同用户（通过不同的浏览器或匿名窗口访问）将拥有各自独立的任务列表。

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_159.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_160.png)

---

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_162.png)

## 总结

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_164.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_166.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_168.png)

本节课我们一起学习了Django Web框架的基础知识。我们从HTTP协议和请求-响应模型讲起，逐步实践了如何创建Django项目和应用程序。我们学习了如何通过视图函数和URL配置来响应不同的网页请求，并利用Django强大的模板系统动态生成HTML内容，包括使用变量、条件判断和循环。

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_170.png)

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_172.png)

我们还探索了如何处理用户通过表单提交的数据，包括使用Django表单类进行便捷的数据验证和渲染。为了管理多个用户的独立数据，我们引入了会话（Session）的概念。最后，我们了解了如何使用模板继承来复用代码结构，以及如何管理CSS等静态文件。

![](img/79b3a35557dd6fe8a6bc1e96c89db2f5_174.png)

通过这些内容，你已经掌握了使用Django构建简单动态Web应用的核心技能。在接下来的课程中，我们将深入探讨数据库集成、用户认证等更高级的主题。