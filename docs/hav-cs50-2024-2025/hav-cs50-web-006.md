# 006：SQL、模型与迁移

![](img/9af736796d8c40401ec301827e4977ab_1.png)

## 概述

在本节课中，我们将学习如何为Web应用添加数据存储能力。我们将从SQL语言的基础知识开始，了解如何创建和操作数据库。然后，我们将学习Django框架中的“模型”概念，这是一种用Python类来代表数据库表的方法。最后，我们将学习“迁移”，这是一种将模型更改应用到数据库的技术。通过结合这些工具，我们将能够构建动态的、数据驱动的Web应用。

## SQL基础

上一节我们介绍了Django框架，它允许我们构建动态Web应用。本节中，我们来看看如何存储和管理应用中的数据，这通常需要使用数据库。

### 数据库与表

在计算机系统中存储数据有多种方式。在关系型数据库中，数据存储在**表**中。每个表由**行**和**列**组成。

为了便于理解，我们假设正在构建一个航空公司的应用，用于跟踪航班和乘客。

以下是一个表示航班数据的示例表：

| ID | Origin | Destination | Duration |
|----|--------|-------------|----------|
| 1  | New York | London | 415 |

*   **列** 代表我们想要记录的数据字段。例如：`Origin`（出发地）、`Destination`（目的地）、`Duration`（时长）。
*   **行** 代表一条具体的数据记录。例如：一行代表一个从纽约飞往伦敦，耗时415分钟的航班。

SQL是一种用于与关系型数据库管理系统交互的数据库语言。流行的系统包括MySQL、PostgreSQL和SQLite。

*   **MySQL和PostgreSQL** 是功能更全面的数据库服务器，通常运行在独立的服务器上，适合大型应用。
*   **SQLite** 是一个轻量级的实现，它将所有数据存储在一个文件中。这使得它在入门和学习时非常方便。Django默认使用SQLite。

### 数据类型

就像Python有整数、字符串等类型一样，SQL数据库中的每个数据也有其类型。SQLite支持的基本类型包括：

![](img/9af736796d8c40401ec301827e4977ab_3.png)

*   **`TEXT`**: 文本字符串，例如城市名。
*   **`INTEGER`**: 整数，如0, 1, 2, -1等。
*   **`REAL`**: 实数，可以包含小数，如2.8。
*   **`NUMERIC`**: 更通用的数字类型，可用于存储布尔值或日期等。
*   **`BLOB`**: 二进制大对象，用于存储图像、音频等二进制文件。

其他数据库系统（如MySQL）支持更多类型，例如`CHAR(size)`（固定长度字符串）、`VARCHAR(size)`（可变长度字符串）以及不同精度的整数（`SMALLINT`, `INT`, `BIGINT`）和浮点数（`FLOAT`, `DOUBLE`）。

### 创建表

我们使用`CREATE TABLE`命令来定义表的结构。

以下是创建`flights`表的SQL语句：

```sql
CREATE TABLE flights (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    origin TEXT NOT NULL,
    destination TEXT NOT NULL,
    duration INTEGER NOT NULL
);
```

![](img/9af736796d8c40401ec301827e4977ab_5.png)

*   `CREATE TABLE flights`: 创建名为`flights`的新表。
*   `id INTEGER PRIMARY KEY AUTOINCREMENT`: 创建一个整数类型的`id`列，作为主键（唯一标识符），并自动递增。
*   `origin TEXT NOT NULL`: 创建一个文本类型的`origin`列，`NOT NULL`约束确保该列不能为空。
*   `destination TEXT NOT NULL` 和 `duration INTEGER NOT NULL` 同理。

以下是常见的列约束：
*   `NOT NULL`: 该列不能为空。
*   `DEFAULT`: 设置默认值。
*   `PRIMARY KEY`: 将该列设为主键。
*   `UNIQUE`: 确保该列所有值都唯一。
*   `CHECK`: 确保值满足特定条件（例如，评分在1-5之间）。

### 操作数据：增删改查

创建表后，我们需要操作其中的数据。以下是四个核心操作：

**1. 插入数据 (INSERT)**

使用`INSERT INTO`命令添加新行。

```sql
INSERT INTO flights (origin, destination, duration) VALUES ('New York', 'London', 415);
```
这条命令向`flights`表添加了一行数据，指定了`origin`、`destination`和`duration`的值。`id`列会自动生成。

**2. 查询数据 (SELECT)**

使用`SELECT`命令从表中检索数据。

*   获取所有数据：
    ```sql
    SELECT * FROM flights;
    ```
*   只选择特定列：
    ```sql
    SELECT origin, destination FROM flights;
    ```
*   添加条件过滤行（`WHERE`子句）：
    ```sql
    SELECT * FROM flights WHERE id = 3;
    SELECT * FROM flights WHERE origin = 'New York';
    SELECT * FROM flights WHERE duration > 500 AND destination = 'Paris';
    SELECT * FROM flights WHERE origin IN ('New York', 'Lima');
    SELECT * FROM flights WHERE origin LIKE '%a%'; -- 查找origin中包含字母'a'的航班
    ```

**3. 更新数据 (UPDATE)**

使用`UPDATE`命令修改现有数据。

```sql
UPDATE flights SET duration = 430 WHERE origin = 'New York' AND destination = 'London';
```
这条命令将所有从纽约飞往伦敦的航班的时长更新为430分钟。

**4. 删除数据 (DELETE)**

使用`DELETE FROM`命令删除行。

```sql
DELETE FROM flights WHERE destination = 'Tokyo';
```
这条命令删除所有目的地为东京的航班。

### 高级查询选项

以下子句可以增强查询功能：
*   `LIMIT`: 限制返回的行数。
*   `ORDER BY`: 按指定列排序结果。
*   `GROUP BY`: 将行分组，常与`COUNT`、`SUM`等聚合函数一起使用。
*   `HAVING`: 对分组后的结果设置条件。

### 实践：在终端中使用SQLite

1.  创建数据库文件：`touch flights.sql`
2.  打开SQLite命令行：`sqlite3 flights.sql`
3.  创建表：
    ```sql
    CREATE TABLE flights (
        id INTEGER PRIMARY KEY AUTOINCREMENT,
        origin TEXT NOT NULL,
        destination TEXT NOT NULL,
        duration INTEGER NOT NULL
    );
    ```
4.  验证表已创建：`.tables`
5.  插入数据：
    ```sql
    INSERT INTO flights (origin, destination, duration) VALUES ('New York', 'London', 415);
    ```
6.  查询数据：`SELECT * FROM flights;`
7.  可以执行更复杂的查询，如`SELECT * FROM flights WHERE origin = 'New York';`

## 关系与多表设计

在实际应用中，数据通常分布在多个相互关联的表中。

### 外键与关系

![](img/9af736796d8c40401ec301827e4977ab_7.png)

假设我们不仅想存储城市名，还想存储机场代码。我们可以创建一个独立的`airports`表，然后在`flights`表中使用**外键**来引用它。

**airports表**
| id | code | city |
|----|------|------|
| 1  | JFK  | New York |
| 2  | LHR  | London |

**flights表 (修改后)**
| id | origin_id | destination_id | duration |
|----|-----------|----------------|----------|
| 1  | 1         | 2              | 415      |

![](img/9af736796d8c40401ec301827e4977ab_9.png)

这里，`flights`表中的`origin_id`和`destination_id`是外键，它们引用`airports`表中的`id`。这种设计避免了数据冗余（如重复城市名），并使数据更规范化。

### 多对多关系

一个乘客可能乘坐多个航班，一个航班也有多个乘客。这是一种**多对多**关系。我们无法在`passengers`表中只用一个`flight_id`列来表示。

![](img/9af736796d8c40401ec301827e4977ab_11.png)

解决方案是使用一个**关联表**（或连接表）。

![](img/9af736796d8c40401ec301827e4977ab_13.png)

![](img/9af736796d8c40401ec301827e4977ab_14.png)

**people表**
| id | first_name | last_name |
|----|------------|-----------|
| 1  | Harry      | Potter    |

**passengers表 (关联表)**
| person_id | flight_id |
|-----------|-----------|
| 1         | 1         |
| 1         | 4         |

这个表只存储人员ID和航班ID的对应关系，从而实现了多对多映射。

![](img/9af736796d8c40401ec301827e4977ab_16.png)

![](img/9af736796d8c40401ec301827e4977ab_18.png)

### 连接查询

为了从多个关联表中获取完整信息，我们使用`JOIN`查询。

![](img/9af736796d8c40401ec301827e4977ab_20.png)

```sql
SELECT first_name, origin, destination
FROM flights
JOIN passengers ON passengers.flight_id = flights.id;
```
这条查询将`flights`表和`passengers`表连接起来，返回乘客名及其航班的出发地和目的地。`ON`子句指定了两个表如何关联。

### 索引

为了提高查询效率（例如频繁按姓氏查找乘客），可以在表上创建**索引**。索引就像书的目录，能加快查找速度，但会增加存储开销并影响写入性能。

![](img/9af736796d8c40401ec301827e4977ab_22.png)

```sql
CREATE INDEX name_index ON passengers (last_name);
```

## SQL安全与并发

![](img/9af736796d8c40401ec301827e4977ab_24.png)

### SQL注入攻击

如果直接将用户输入拼接到SQL查询中，攻击者可以输入恶意内容来操纵查询，从而绕过身份验证或破坏数据。这称为SQL注入攻击。

**危险示例：**
```python
# 假设从表单获取用户名和密码
username = request.form['username']
password = request.form['password']
query = f"SELECT * FROM users WHERE username = '{username}' AND password = '{password}'"
# 如果用户输入用户名: hacker' --
# 查询会变成: SELECT * FROM users WHERE username = 'hacker' --' AND password = '...'
# `--`在SQL中是注释，因此密码检查被绕过。
```

**解决方案：**
1.  **参数化查询/转义字符**：使用数据库库提供的安全方法，而不是字符串拼接。
2.  **使用ORM**：这正是Django模型要做的事——它提供了一个抽象层，让我们无需编写原始SQL。

![](img/9af736796d8c40401ec301827e4977ab_26.png)

![](img/9af736796d8c40401ec301827e4977ab_27.png)

![](img/9af736796d8c40401ec301827e4977ab_28.png)

### 竞态条件

当多个操作（例如两个用户同时“喜欢”一个帖子）并发执行时，可能会发生竞态条件，导致数据不一致。

![](img/9af736796d8c40401ec301827e4977ab_30.png)

**解决方案：**
使用**锁**或**事务**来确保一系列数据库操作作为一个整体执行，期间其他操作必须等待。

![](img/9af736796d8c40401ec301827e4977ab_32.png)

![](img/9af736796d8c40401ec301827e4977ab_34.png)

## Django模型

![](img/9af736796d8c40401ec301827e4977ab_36.png)

![](img/9af736796d8c40401ec301827e4977ab_38.png)

![](img/9af736796d8c40401ec301827e4977ab_40.png)

现在，我们转向Django，看看它如何通过“模型”抽象SQL操作，让我们用Python对象来操作数据库。

### 创建模型

在Django应用中，我们在`models.py`文件里定义模型。每个模型类对应一张数据库表。

![](img/9af736796d8c40401ec301827e4977ab_42.png)

1.  创建Django项目和应用：
    ```bash
    django-admin startproject airline
    cd airline
    python manage.py startapp flights
    ```
2.  在`settings.py`的`INSTALLED_APPS`中添加`'flights'`。
3.  配置项目和应用级别的`urls.py`。
4.  在`flights/models.py`中定义`Flight`模型：
    ```python
    from django.db import models

    class Flight(models.Model):
        origin = models.CharField(max_length=64)
        destination = models.CharField(max_length=64)
        duration = models.IntegerField()
    ```
    这个`Flight`类继承自`models.Model`，它有三个字段，分别对应数据库表中的三列。

### 迁移

模型定义是Python代码，我们需要将其同步到数据库。这个过程分为两步：

![](img/9af736796d8c40401ec301827e4977ab_44.png)

![](img/9af736796d8c40401ec301827e4977ab_45.png)

1.  **创建迁移文件**：根据模型变化生成操作指令。
    ```bash
    python manage.py makemigrations
    ```
    这会在`migrations/`文件夹下生成一个文件（如`0001_initial.py`），其中包含创建`Flight`表的指令。

![](img/9af736796d8c40401ec301827e4977ab_47.png)

2.  **应用迁移**：执行迁移文件中的指令，实际修改数据库。
    ```bash
    python manage.py migrate
    ```
    执行后，会创建一个SQLite数据库文件（如`db.sqlite3`），其中包含`flights`表。

![](img/9af736796d8c40401ec301827e4977ab_49.png)

![](img/9af736796d8c40401ec301827e4977ab_51.png)

![](img/9af736796d8c40401ec301827e4977ab_53.png)

### 使用Django Shell操作数据

![](img/9af736796d8c40401ec301827e4977ab_55.png)

![](img/9af736796d8c40401ec301827e4977ab_57.png)

我们可以使用Django shell来交互式地操作模型，就像在Python中操作对象一样。

![](img/9af736796d8c40401ec301827e4977ab_59.png)

1.  打开shell：
    ```bash
    python manage.py shell
    ```
2.  导入模型并操作：
    ```python
    from flights.models import Flight

    # 创建并保存一个新航班
    f = Flight(origin="New York", destination="London", duration=415)
    f.save()

    # 查询所有航班
    all_flights = Flight.objects.all()
    print(all_flights) # 默认显示为 <QuerySet [<Flight: Flight object (1)>]>

    # 获取第一个航班并访问其属性
    first_flight = Flight.objects.first()
    print(first_flight.origin) # New York
    print(first_flight.duration) # 415

    # 删除航班
    first_flight.delete()
    ```

![](img/9af736796d8c40401ec301827e4977ab_61.png)

![](img/9af736796d8c40401ec301827e4977ab_62.png)

3.  改进模型显示：在`Flight`模型中添加`__str__`方法，让对象显示更友好。
    ```python
    class Flight(models.Model):
        # ... 字段定义 ...
        def __str__(self):
            return f"{self.id}: {self.origin} to {self.destination}"
    ```
    现在，查询结果会显示为 `1: New York to London`。

### 定义关系

让我们用Django模型实现之前讨论的`Airport`和`Flight`关系，以及`Passenger`的多对多关系。

1.  修改`models.py`，添加`Airport`模型并修改`Flight`模型：
    ```python
    class Airport(models.Model):
        code = models.CharField(max_length=3)
        city = models.CharField(max_length=64)

        def __str__(self):
            return f"{self.city} ({self.code})"

    class Flight(models.Model):
        # 将origin和destination改为外键，引用Airport模型
        origin = models.ForeignKey(Airport, on_delete=models.CASCADE, related_name="departures")
        destination = models.ForeignKey(Airport, on_delete=models.CASCADE, related_name="arrivals")
        duration = models.IntegerField()

        def __str__(self):
            return f"{self.id}: {self.origin} to {self.destination}"
    ```
    *   `ForeignKey`: 定义多对一关系。一个航班有一个出发机场和一个到达机场，但一个机场可以有多个出发或到达航班。
    *   `on_delete=models.CASCADE`: 如果引用的机场被删除，相关的航班也会被删除。
    *   `related_name`: 允许反向查询。通过`airport.departures.all()`可以获取从该机场出发的所有航班。

2.  创建`Passenger`模型，与`Flight`建立多对多关系：
    ```python
    class Passenger(models.Model):
        first = models.CharField(max_length=64)
        last = models.CharField(max_length=64)
        flights = models.ManyToManyField(Flight, blank=True, related_name="passengers")

        def __str__(self):
            return f"{self.first} {self.last}"
    ```
    *   `ManyToManyField`: 定义多对多关系。Django会自动在后台创建关联表。
    *   `related_name="passengers"`: 允许通过`flight.passengers.all()`获取该航班的所有乘客。

3.  生成并应用新的迁移：
    ```bash
    python manage.py makemigrations
    python manage.py migrate
    ```

4.  在shell中体验关系操作：
    ```python
    from flights.models import *

    # 创建机场
    jfk = Airport(code="JFK", city="New York")
    jfk.save()
    lhr = Airport(code="LHR", city="London")
    lhr.save()

    # 创建航班，关联机场
    f = Flight(origin=jfk, destination=lhr, duration=415)
    f.save()

    # 访问关联属性
    print(f.origin.city) # New York
    print(lhr.arrivals.all()) # 获取所有到达伦敦的航班

    # 创建乘客并关联航班
    harry = Passenger(first="Harry", last="Potter")
    harry.save()
    harry.flights.add(f) # 将乘客harry添加到航班f
    print(f.passengers.all()) # 获取航班f的所有乘客
    ```

## 构建Web界面

### 显示航班列表

![](img/9af736796d8c40401ec301827e4977ab_64.png)

1.  在`views.py`中创建视图函数，查询所有航班并传递给模板。
    ```python
    from .models import Flight

    def index(request):
        flights = Flight.objects.all()
        return render(request, "flights/index.html", {"flights": flights})
    ```
2.  创建模板`flights/index.html`来显示航班列表。
    ```html
    <h1>Flights</h1>
    <ul>
        {% for flight in flights %}
            <li>
                <a href="{% url 'flight' flight.id %}">
                    Flight {{ flight.id }}: {{ flight.origin }} to {{ flight.destination }}
                </a>
            </li>
        {% endfor %}
    </ul>
    ```

![](img/9af736796d8c40401ec301827e4977ab_66.png)

![](img/9af736796d8c40401ec301827e4977ab_67.png)

### 显示单个航班详情

![](img/9af736796d8c40401ec301827e4977ab_69.png)

1.  在`urls.py`中添加带参数的路径：`path("<int:flight_id>", views.flight, name="flight")`。
2.  在`views.py`中创建`flight`视图函数，根据`flight_id`获取特定航班及其乘客。
    ```python
    def flight(request, flight_id):
        flight = Flight.objects.get(pk=flight_id)
        passengers = flight.passengers.all()
        return render(request, "flights/flight.html", {
            "flight": flight,
            "passengers": passengers
        })
    ```
3.  创建模板`flights/flight.html`显示航班详情和乘客列表。

![](img/9af736796d8c40401ec301827e4977ab_71.png)

### 添加乘客到航班

![](img/9af736796d8c40401ec301827e4977ab_73.png)

![](img/9af736796d8c40401ec301827e4977ab_75.png)

1.  在`urls.py`中添加路径：`path("<int:flight_id>/book", views.book, name="book")`。
2.  在`views.py`中创建`book`视图函数，处理表单提交（POST请求）。
    ```python
    from django.http import HttpResponseRedirect
    from django.urls import reverse
    from .models import Flight, Passenger

    def book(request, flight_id):
        if request.method == "POST":
            flight = Flight.objects.get(pk=flight_id)
            # 获取表单中提交的乘客ID
            passenger_id = int(request.POST["passenger"])
            passenger = Passenger.objects.get(pk=passenger_id)
            # 将乘客添加到该航班
            passenger.flights.add(flight)
            return HttpResponseRedirect(reverse("flight", args=(flight_id,)))
    ```
3.  在航班详情页的模板中，添加一个表单，列出所有**未乘坐该航班**的乘客供选择。
    ```python
    # 在flight视图中，需要获取非乘客列表
    non_passengers = Passenger.objects.exclude(flights=flight).all()
    # 并传递给模板
    ```
    ```html
    <!-- 在flight.html模板中添加表单 -->
    <h2>Add Passenger</h2>
    <form action="{% url 'book' flight.id %}" method="post">
        {% csrf_token %}
        <select name="passenger">
            {% for passenger in non_passengers %}
                <option value="{{ passenger.id }}">{{ passenger }}</option>
            {% endfor %}
        </select>
        <input type="submit" value="Book Flight">
    </form>
    ```

![](img/9af736796d8c40401ec301827e4977ab_77.png)

## Django Admin 管理界面

![](img/9af736796d8c40401ec301827e4977ab_79.png)

Django提供了一个功能强大的内置管理界面，用于管理模型数据，无需自己编写后台。

1.  创建超级用户：
    ```bash
    python manage.py createsuperuser
    ```
2.  在`admin.py`中注册模型：
    ```python
    from django.contrib import admin
    from .models import Airport, Flight, Passenger

    admin.site.register(Airport)
    admin.site.register(Flight)
    admin.site.register(Passenger)
    ```
3.  运行服务器，访问`/admin`，使用超级用户登录。现在你可以在这里直观地添加、修改、删除航班、机场和乘客数据。
4.  自定义Admin界面（可选）：
    ```python
    # 在admin.py中
    class FlightAdmin(admin.ModelAdmin):
        list_display = ("id", "origin", "destination", "duration") # 列表页显示更多字段

    class PassengerAdmin(admin.ModelAdmin):
        filter_horizontal = ("flights",) # 为多对多字段使用更友好的水平选择器

    admin.site.register(Flight, FlightAdmin)
    admin.site.register(Passenger, PassengerAdmin)
    ```

## 用户认证

Django内置了强大的用户认证系统。

![](img/9af736796d8c40401ec301827e4977ab_81.png)

![](img/9af736796d8c40401ec301827e4977ab_83.png)

1.  创建用户管理应用：
    ```bash
    python manage.py startapp users
    ```
2.  将其添加到`INSTALLED_APPS`并配置URL。
3.  实现视图（`users/views.py`）：
    ```python
    from django.contrib.auth import authenticate, login, logout
    from django.http import HttpResponseRedirect
    from django.urls import reverse
    from django.shortcuts import render

    def index(request):
        # 如果用户未登录，重定向到登录页
        if not request.user.is_authenticated:
            return HttpResponseRedirect(reverse("login"))
        # 已登录则显示用户信息
        return render(request, "users/user.html")

    def login_view(request):
        if request.method == "POST":
            username = request.POST["username"]
            password = request.POST["password"]
            user = authenticate(request, username=username, password=password)
            if user is not None:
                login(request, user)
                return HttpResponseRedirect(reverse("index"))
            else:
                return render(request, "users/login.html", {
                    "message": "Invalid credentials."
                })
        # GET请求，显示登录表单
        return render(request, "users/login.html")

    def logout_view(request):
        logout(request)
        return render(request, "users/login.html", {
            "message": "Logged out."
        })
    ```
4.  创建登录模板（`users/login.html`）和用户信息模板（`users/user.html`）。
5.  登录后，可以在模板中使用`{{ request.user }}`访问当前用户对象，显示用户名、邮箱等信息。

![](img/9af736796d8c40401ec301827e4977ab_85.png)

## 总结

![](img/9af736796d8c40401ec301827e4977ab_87.png)

本节课中我们一起学习了Web应用开发中数据存储的核心知识。

我们首先了解了**SQL**的基础，包括如何创建表、插入、查询、更新和删除数据，以及多表关系设计和连接查询。

![](img/9af736796d8c40401ec301827e4977ab_89.png)

![](img/9af736796d8c40401ec301827e4977ab_91.png)

然后，我们深入学习了Django的**模型**系统，它允许我们用Python类来定义数据库结构，并通过操作对象来间接操作数据库，无需编写复杂的SQL语句。

![](img/9af736796d8c40401ec301827e4977ab_93.png)

接着，我们掌握了**迁移**的概念和流程，即通过`makemigrations`和`migrate`命令将模型的变化同步到数据库。

![](img/9af736796d8c40401ec301827e4977ab_95.png)

我们还利用这些知识构建了一个简单的航空公司应用，实现了航班和乘客的显示与管理，并体验了Django强大的**Admin管理后台**和内置的**用户认证系统**。

![](img/9af736796d8c40401ec301827e4977ab_97.png)

![](img/9af736796d8c40401ec301827e4977ab_99.png)

通过结合SQL、Django模型和迁移，我们能够高效、安全地构建出功能丰富、数据驱动的动态Web应用程序。