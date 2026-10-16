
## MVC Design Patterns

- **Components:** Model, View, Controller
- **Connectors:** Explicit Invocation, Implicit Invocation or other mechanisms (e.g. HTTP protocol)

![](img/95717dc23f76db2057b9aa0c49790307_570_0.png)

MVC模式架构图

## MVC Design Patterns

- • 模型的责任
- • Model is responsible for
  - Providing the data from the database and saving the data into the data store (负责从数据库取出数据，并且赋予数据变量).
  - All the business logics are implemented in the Model (负责任务逻辑实现).
  - Data entered by the user through View are checked in the model before saving into the database (负责数据验证，然后将数据存入数据库).

## MVC Design Patterns

- 视图的责任
- View is responsible for:
  - Taking the input from the user (获取用户输入)
  - Dispatching the request to the controller, and then (向controller发送处理请求)
  - Receiving response from the controller and displaying the result to the user (接收来自Controller的反馈并将model的处理结果显示给用户)
- Multiple views can exist for a single model for different purposes.(一个model可能有多个View)

## MVC Design Patterns

- 控制器的责任
- Controller is responsible for:
  – Receiving the request from client (接收来自客户的请求)
  – Executing the appropriate business logic from the Model (调用model业务逻辑)
  – Producing the output to the user using the View component (调用View显示执行结果)

## MVC Design Patterns

调用Model中的方法，获得数据 (因为要更新视图)

1)选择视图 2)获取用户输入

调用Model中的业务逻辑方法

# MVC模式架构图-交互情况

## MVC Design Patterns

- Two principal separations:
  - Separating the presentation from the model
  - Separating the controller from the view

## MVC Design Patterns

负责用户输入

View可以不必调用 Controller

当代的一种MVC模式架构类图-使用了观察者模式

![](img/95717dc23f76db2057b9aa0c49790307_577_0.png)

## MVC的优点

- 1) 容易增加或者改变视图

事务逻辑被封装在Model中，所以在新增一个视图的时候，不必要改动模型，而是因为业务逻辑都是一样的，所以只需要新增一个视图类即可。

![](img/95717dc23f76db2057b9aa0c49790307_578_0.png)

## MVC的优点

2) 容易独立地更新每个独立的软件模块
由于一个应用被分离为三个软件模块，因此，我们可以独立地改变其中的一个模块，而不影响其它两个模块。例如，一个应用的业务流程或者业务规则的改变只需改动MVC的模型层。

3) 代码易开发易维护 Make source code more flexible and maintainable

4) 业务逻辑更易测试 Make it very easy to test all the domain logic. Because Non-visual objects are usually easier to test than visual ones

## MVC Frameworks

- J2EE:
  - Struts
  - Spring MVC
- PHP
  - CakePHP
  - Strusts4php
- C#.NET
  - Girders
- Ruby on Rails

## Design Examples Using the MVC Design Pattern
MVC Architecture

## 网上二手车拍卖系统的设计: 方案3

## 方案3: 采用MVC模式-使用观察者机制的情况，用户输入界面和两个显示视图分别独立显示

• 将事务逻辑部分和用户界面部分分开，采用MVC模式。设计如下：

- CarAuctionGUI, provide user input interface, represent user;
- CarModel, Model part, encapsulate transaction logic functions
- CarBitView, View part, display user-given auction price
- CarGUIView, View part, display car pictures
- Controller, controller part, process user input, call model and view

![](img/95717dc23f76db2057b9aa0c49790307_583_0.png)

用户输入界面原型（Prototype）-点击search按钮的时候

## 网上二手车拍卖系统的设计: 方案3

## Car information- Observer 1

![](img/95717dc23f76db2057b9aa0c49790307_584_0.png)

## Honda Accord

Made in 2005, used by the Department of defense. Mileage:

# 二手车信息显示界面原型 (Prototype)

用户输入界面原型（Prototype）-点击bit按钮的时候

## 网上二手车拍卖系统的设计: 方案3

## Car Bit Info View- Observer 2

Bits offered:

Bit price for Honda Accord-2005=3860

# 二手车当前拍卖价格显示界面原型（Prototype）

## CarAuctionGUI
getSelectedCar(): String
getBitPrice(): String
getCarList(): String[]
setUpComboBox(String[] carList): void

## Controller
objCarGUI: CarAuctionGUI
cm: CarModel
carPrice: String
actionPerformed(ActionEvent e)

## <<interface>>
Observable
+register(Observer obs): void
+notifyObservers(): void

## CarModel
String[] carNameList;
String bitPrice;
+setCarList(String[] cars): void
+getCarList(): String[]
+setSelectedCar(String sCar): void
+getSelectedCar(): String
+setBitPrice(String bPrice): void
+getBitPrice(): String
+setCarFileURL(): void
+getCarFileURL(): URL
+setupImageIcon(): void
+getImageIcon(): ImageIcon
+register(Observer obs): void
+notifyObservers(): void

## <<interface>>
Observer
update(Observable subject): void

## CarGUIInfoView
model: CarModel
+update(s): void

## CarBitInfoView
model: CarModel
+update(s): void

二手车拍卖系统的类图设计
