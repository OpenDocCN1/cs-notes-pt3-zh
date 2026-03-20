# 009：测试与CI/CD 🧪

![](img/d2d778b8327db64cb9b1861e971462ca_1.png)

![](img/d2d778b8327db64cb9b1861e971462ca_3.png)

在本节课中，我们将学习软件开发中的两个重要最佳实践：**测试**与**持续集成/持续交付**。我们将探讨如何验证代码的正确性，以及如何高效地协作和部署应用。

![](img/d2d778b8327db64cb9b1861e971462ca_5.png)

![](img/d2d778b8327db64cb9b1861e971462ca_6.png)

---

![](img/d2d778b8327db64cb9b1861e971462ca_8.png)

## 概述

到目前为止，我们已经学习了使用HTML、CSS、Python（Django框架）和JavaScript来设计和构建交互式Web应用。今天，我们将转向**软件工程的最佳实践**，特别是当应用规模增长时，开发者实际使用的工具和技术。我们将从**测试**开始，讨论如何验证代码的正确性，然后过渡到**CI/CD**，即持续集成和持续交付，以确保开发工作能够被高效地测试和部署。

---

## 测试基础

测试的核心思想是验证和确保开发者编写的代码是正确的。我们希望确保函数按预期工作，网页按预期表现，并且能够随着程序变得复杂，高效地测试代码。

### 使用 `assert` 进行简单测试

在Python中，我们可以使用 `assert` 语句来声明某个条件应为真。如果条件不为真，`assert` 会抛出一个异常。

```python
def square(x):
    return x * x

![](img/d2d778b8327db64cb9b1861e971462ca_10.png)

assert square(10) == 100
```

![](img/d2d778b8327db64cb9b1861e971462ca_12.png)

如果 `square(10)` 的结果等于100，程序会正常继续。如果不等于，则会抛出 `AssertionError`。

![](img/d2d778b8327db64cb9b1861e971462ca_14.png)

![](img/d2d778b8327db64cb9b1861e971462ca_16.png)

### 测试驱动开发

![](img/d2d778b8327db64cb9b1861e971462ca_18.png)

测试驱动开发是一种在编写代码时始终考虑测试的实践。一个最佳实践是：当你在自己的程序中遇到一个bug时，首先修复它，然后编写一个测试来验证新的行为符合预期。随着时间的推移，这些测试会不断积累。当你继续开发项目时，可以随时运行这些现有的测试，以确保后续的任何新更改或新增功能不会破坏已有的功能。

![](img/d2d778b8327db64cb9b1861e971462ca_20.png)

![](img/d2d778b8327db64cb9b1861e971462ca_21.png)

---

## 编写更复杂的测试

让我们尝试编写一个比平方函数更复杂的函数，例如一个检查数字是否为质数的函数。

```python
import math

def is_prime(n):
    if n < 2:
        return False
    for i in range(2, int(math.sqrt(n)) + 1):
        if n % i == 0:
            return False
    return True
```

我们可以手动测试这个函数，但更好的方法是编写一个测试脚本来自动化这个过程。

---

## 使用 `unittest` 框架

![](img/d2d778b8327db64cb9b1861e971462ca_23.png)

Python内置的 `unittest` 库可以帮助我们快速编写测试，并自动运行它们。

![](img/d2d778b8327db64cb9b1861e971462ca_25.png)

![](img/d2d778b8327db64cb9b1861e971462ca_27.png)

```python
import unittest
from prime import is_prime

![](img/d2d778b8327db64cb9b1861e971462ca_29.png)

class PrimeTestCase(unittest.TestCase):
    def test_is_prime_one(self):
        self.assertFalse(is_prime(1))

    def test_is_prime_two(self):
        self.assertTrue(is_prime(2))

    def test_is_prime_twenty_five(self):
        self.assertFalse(is_prime(25))

if __name__ == '__main__':
    unittest.main()
```

运行这个测试文件，`unittest` 会执行所有测试方法，并报告哪些通过，哪些失败。

---

![](img/d2d778b8327db64cb9b1861e971462ca_31.png)

![](img/d2d778b8327db64cb9b1861e971462ca_33.png)

## 在Django应用中进行测试

![](img/d2d778b8327db64cb9b1861e971462ca_35.png)

在Django中，我们可以为模型、视图和整个应用流程编写测试。

![](img/d2d778b8327db64cb9b1861e971462ca_37.png)

![](img/d2d778b8327db64cb9b1861e971462ca_39.png)

### 测试模型方法

![](img/d2d778b8327db64cb9b1861e971462ca_41.png)

假设我们有一个 `Flight` 模型，并定义了一个 `is_valid_flight` 方法来验证航班数据的有效性。

![](img/d2d778b8327db64cb9b1861e971462ca_43.png)

![](img/d2d778b8327db64cb9b1861e971462ca_45.png)

```python
# models.py
class Flight(models.Model):
    origin = models.ForeignKey(Airport, on_delete=models.CASCADE, related_name="departures")
    destination = models.ForeignKey(Airport, on_delete=models.CASCADE, related_name="arrivals")
    duration = models.IntegerField()

    def is_valid_flight(self):
        return self.origin != self.destination and self.duration > 0
```

### 编写Django测试

Django为每个应用提供了一个 `tests.py` 文件，用于编写测试。

```python
# tests.py
from django.test import TestCase
from .models import Airport, Flight

class FlightTestCase(TestCase):
    def setUp(self):
        # 创建测试数据
        a1 = Airport.objects.create(code="AAA", city="City A")
        a2 = Airport.objects.create(code="BBB", city="City B")
        Flight.objects.create(origin=a1, destination=a2, duration=100)
        Flight.objects.create(origin=a1, destination=a1, duration=200)
        Flight.objects.create(origin=a1, destination=a2, duration=-100)

    def test_departures_count(self):
        a = Airport.objects.get(code="AAA")
        self.assertEqual(a.departures.count(), 3)

    def test_valid_flight(self):
        a1 = Airport.objects.get(code="AAA")
        a2 = Airport.objects.get(code="BBB")
        f = Flight.objects.get(origin=a1, destination=a2, duration=100)
        self.assertTrue(f.is_valid_flight())

    def test_invalid_flight_destination(self):
        a1 = Airport.objects.get(code="AAA")
        f = Flight.objects.get(origin=a1, destination=a1)
        self.assertFalse(f.is_valid_flight())
```

![](img/d2d778b8327db64cb9b1861e971462ca_47.png)

使用 `python manage.py test` 命令运行所有测试。Django会创建一个独立的测试数据库，运行测试后将其销毁，不会影响生产数据。

---

![](img/d2d778b8327db64cb9b1861e971462ca_49.png)

![](img/d2d778b8327db64cb9b1861e971462ca_51.png)

![](img/d2d778b8327db64cb9b1861e971462ca_52.png)

![](img/d2d778b8327db64cb9b1861e971462ca_53.png)

## 测试Web页面和用户交互

![](img/d2d778b8327db64cb9b1861e971462ca_55.png)

![](img/d2d778b8327db64cb9b1861e971462ca_57.png)

除了测试后端逻辑，我们还需要测试前端页面和用户交互。我们可以使用Selenium等工具进行浏览器自动化测试。

![](img/d2d778b8327db64cb9b1861e971462ca_59.png)

![](img/d2d778b8327db64cb9b1861e971462ca_60.png)

![](img/d2d778b8327db64cb9b1861e971462ca_62.png)

![](img/d2d778b8327db64cb9b1861e971462ca_63.png)

![](img/d2d778b8327db64cb9b1861e971462ca_65.png)

![](img/d2d778b8327db64cb9b1861e971462ca_67.png)

### 使用Selenium进行浏览器测试

Selenium允许我们通过代码模拟用户在浏览器中的交互。

![](img/d2d778b8327db64cb9b1861e971462ca_69.png)

![](img/d2d778b8327db64cb9b1861e971462ca_70.png)

```python
from selenium import webdriver
import unittest

class CounterTest(unittest.TestCase):
    def setUp(self):
        self.driver = webdriver.Chrome()

    def test_title(self):
        self.driver.get("http://localhost:8000")
        self.assertEqual(self.driver.title, "Counter")

    def test_increase(self):
        self.driver.get("http://localhost:8000")
        increase_button = self.driver.find_element_by_id("increase")
        increase_button.click()
        h1 = self.driver.find_element_by_tag_name("h1")
        self.assertEqual(h1.text, "1")

    def tearDown(self):
        self.driver.quit()
```

这个测试会打开浏览器，点击按钮，并验证页面内容是否按预期更新。

---

## 持续集成与持续交付

上一节我们介绍了如何编写测试来验证代码。本节中，我们来看看如何利用这些测试来实现高效的团队协作和部署，即CI/CD。

### 持续集成

![](img/d2d778b8327db64cb9b1861e971462ca_72.png)

持续集成是指频繁地将代码合并到主分支，并在代码推送时自动运行单元测试。这种做法可以减少大规模合并时的冲突，并通过自动化测试立即发现新代码引入的问题。

### 持续交付

持续交付是指拥有较短的发布周期，频繁地向用户发布新功能。这有助于快速将新功能推向市场，并在出现问题时更容易定位。

![](img/d2d778b8327db64cb9b1861e971462ca_74.png)

![](img/d2d778b8327db64cb9b1861e971462ca_76.png)

### 使用GitHub Actions实现CI

GitHub Actions允许我们创建工作流，在特定事件（如推送代码）发生时自动执行任务。

```yaml
# .github/workflows/ci.yml
name: Testing

![](img/d2d778b8327db64cb9b1861e971462ca_78.png)

on: [push]

![](img/d2d778b8327db64cb9b1861e971462ca_80.png)

![](img/d2d778b8327db64cb9b1861e971462ca_82.png)

jobs:
  test-project:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Run Django Unit Tests
        run: |
          pip install django
          python manage.py test
```

![](img/d2d778b8327db64cb9b1861e971462ca_84.png)

这个工作流会在每次推送代码时，在一个Ubuntu虚拟机上检出代码，安装Django，然后运行测试。

---

## 使用Docker容器化应用

为了确保开发、测试和生产环境的一致性，我们可以使用Docker将应用及其依赖项打包到容器中。

![](img/d2d778b8327db64cb9b1861e971462ca_86.png)

### 创建Dockerfile

Dockerfile定义了如何构建应用镜像。

```dockerfile
# Dockerfile
FROM python:3
COPY . /usr/src/app
WORKDIR /usr/src/app
RUN pip install -r requirements.txt
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
```

### 使用Docker Compose组合服务

对于需要多个服务的应用（如Web应用和数据库），可以使用Docker Compose。

```yaml
# docker-compose.yml
version: '3'
services:
  db:
    image: postgres
  web:
    build: .
    command: python manage.py runserver 0.0.0.0:8000
    volumes:
      - .:/usr/src/app
    ports:
      - "8000:8000"
    depends_on:
      - db
```

![](img/d2d778b8327db64cb9b1861e971462ca_88.png)

![](img/d2d778b8327db64cb9b1861e971462ca_90.png)

运行 `docker-compose up` 可以同时启动Web应用和PostgreSQL数据库容器。

![](img/d2d778b8327db64cb9b1861e971462ca_92.png)

---

![](img/d2d778b8327db64cb9b1861e971462ca_94.png)

![](img/d2d778b8327db64cb9b1861e971462ca_96.png)

## 总结

![](img/d2d778b8327db64cb9b1861e971462ca_98.png)

在本节课中，我们一起学习了软件工程中的关键最佳实践。我们首先探讨了**测试**的重要性，学习了如何使用 `assert` 语句、`unittest` 框架以及在Django中编写测试来验证代码的正确性。接着，我们介绍了**持续集成和持续交付**的概念，了解了如何通过频繁合并代码和自动化测试来提升团队协作效率，以及如何使用短发布周期快速交付价值。最后，我们接触了**Docker**，它通过容器化技术确保了开发、测试和生产环境的一致性，使得应用的部署和扩展更加可靠和高效。这些实践是构建和维护现代、健壮且可扩展的Web应用程序的基石。