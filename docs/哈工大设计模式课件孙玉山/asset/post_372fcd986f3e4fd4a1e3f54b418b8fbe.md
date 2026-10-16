
## 网上二手车拍卖系统的设计

MVC pattern demo-Car auction

- Cars: Honda Civic-2006
- Search
- Exit
- Bid
- Bid price for each car will be shown here
- Bid price for Honda Civic-2006: 5530

### Honda Civic

Made in 2006, used by the New York State government. Mileage: 40,000 miles. 5-speed manual transmission (25 city/36 highway), 140-hp, 1.8-Liter.

![](img/95717dc23f76db2057b9aa0c49790307_555_0.png)

The prototype of the graphical user interface

![](img/95717dc23f76db2057b9aa0c49790307_556_0.png)

Different data displays

### 网上二手车拍卖系统的设计：方案1

- **Design 1:** 仅仅使用一个Java类实现全部功能
  - use only one java class to implement all the functions
- Produce user interface
- All the business logics are in this java class

设计方案1: 只用一个Java文件

包含GUI、业务逻辑、数据库访问

JPanel

CarAuctionGUI

```
+getSelectedCar(): String //get user input
+getBidPrice(): String //get user input bid price
+extractCarList(): String[] //display car list
+setUpCarList(JComboBox cmbCarList, String[] carList) //add car list onto cmbCarList
+constructCarFileUrl(String carChosen): URL //produce a URL based on car name
+updateCarDescription(JEditorPane editorPane, URL url) //update car description
+showBidPrice(JTextArea bidShownText, String price) //display bid price
+produceCarImageIcon(String carChosen): ImageIcon //produce image icon for car
+updateCarPicture(JLabel imgLabel, ImageIcon imgIcon) //update car picture
#createImageIcon(String path): ImageIcon
```

Design 1: use only one java GUI file to implement all the functions

**缺点 Drawbacks:**

- 1. 可扩展性不好 Poor extensibility
  - When new function is added, need to recompile the whole class
  - When you modify something, need recompile whole class
- 2. Only one user GUI, and actually sometimes multiple GUIs are needed

Solution: redesign

### 网上二手车拍卖系统的设计：方案2

软件设计方案2: 将整个项目设计为两个组件

- 用户界面CarAuctionGUI:
  - a) 用户输入功能
  - b) 查询结果
- 类AuctionFunctions:
  - 1. 从一个文件夹中提取车的信息描述文件
  - 2. 将该文件显示到用户界面上
  - 3. 从一个文件夹中提取车的图片文件
  - 4. 将该图片文件显示到用户界面上
  - 5. 将竞拍价格显示到屏幕上
  - 6. 所有的业务逻辑方法

![](img/95717dc23f76db2057b9aa0c49790307_561_0.png)

软件设计方案2: 将整个项目设计为两个组件

### 设计方案2的优点：实现了责任分离

- 1. 在用户界面程序中，除了搭建所有的图形组件外，仅仅提供了用户输入的获取功能：
  - getSelectedCar(): String
  - getBidPrice(): String
- 2. 将所有其它的功能都放到单独的一个类 AuctionFunctions中

### 设计方案2的缺点

在一个类AuctionFunctions中，集中了

- 业务逻辑
- 显示功能
- 其它的所有辅助功能

造成了接口污染

### MVC Design Patterns

### 新设计方案考虑：

- 1. 要求在输入方面有可扩展性，例如
  - 键盘输入，
  - 图形界面上的按钮输入
  - 手机、平板的触摸屏输入
- 2. 对于汽车信息，允许有不同的显示
  - 图片显示
  - 文字显示
  - 性能分析
  - 销售情况（柱形图，饼形图）
- 3. 希望将所有的业务逻辑都封装到一个类中

- 解决方法：使用Model-View-Controller (MVC)设计模式。
- MVC (Model-View-Controller)设计模式将一个互动的应用程序分成3部分：
  - 模型(Model)，包含核心功能与数据
  - 视图(View)，负责用户输入，并且为用户显示信息
  - 控制器(Controller)，处理用户输入。

### Theory of the MVC design pattern

- **定义：** In software engineering, Model–View–Controller (MVC) is an architectural pattern that splits interactions between users and applications into three roles:
  - the Model (business logic),
  - the View (user interface), and
  - the Controller (user input).
- This separation of concerns facilitates the independent development, testing, and maintenance of each role (关注点分离：模型、视图和控制器).

- MVC设计模式将系统分成3个组件：Model, View, Controller
- <<updates>> 更新视图
- <<manipulates>> 改变模型状态
- View不负责输入，仅仅显示输出
- 用户输入命令行
- <<uses>>

MVC设计模式的较早的应用交互情况

- **MVC历史**

MVC was first described in 1979 by Trygve Reenskaug, then working on Smalltalk at Xerox PARC (施乐帕克研究中心).

- Since the late 1990s, MVC is commonly classified as an architectural pattern.
