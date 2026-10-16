

## 3.3 泛化关系

- ☑ 泛化是指类间的结构关系、亲子关系
  - ◆ 子类继承父类所具有的属性、操作和关联
- ☑ 分析阶段的泛化关系主要来自于业务对象模型，针对实体类，结合业务领域的需求，从两个方面来提取泛化关系：
  - ◆ 是否有类似的结构和行为的类，从而可以抽取出通用的结构和行为构成父类
  - ◆ 单个实体类是否存在一些不同类别的结构和行为，从而可以将这些不同类别的结构抽取出构成不同的子类

## 实例：实体类间的聚合和泛化

![](img/32b9da3a6e0f048e7dd2e9664c939f9e_390_0.png)

## 4. 限定分析机制

### 建立分析类和分析机制的对应图

| 分析类 | 分析机制 | 说明 |
|---|---|---|
| 申请控制类 | 分布 | 前台服务员可以通过本地客户机访问服务器上的旅游团和路线信息 |
| 导出财务信息控制类 | 遗留接口 | 导出的财务信息需要导入到遗留的财务系统 |
| 旅游团、路线申请 | 持久性<br>持久性 | 旅游团和路线信息需存储在数据库中<br>申请相关信息需存储在数据库中 |
| 支付明细 | 持久性、安全性、遗留接口 | 支付明细信息需存储在数据库中，并不允许随意修改，同时要与外部财务系统保持一致 |
| 参加人、联系人 | 持久性 | 参加人和联系人等信息需存储在数据库中 |

### 描述分析机制特性

| 类 | 分析机制 | 特征 | 特征值 |
|---|---|---|---|
| 申请类 | 持久性 | 粒度 | 单个申请数据约1到5KB |
| 申请类 | 持久性 | 容量 | 每天约1000个申请，高峰时约5000个 |
| 申请类 | 持久性 | 访问频率 | 读取：每天5000次，写入：每天1000次，更新：每天1000次，删除：每天1000次 |
| 申请类 | 持久性 | 访问机制 | 主要按申请编号查询，也可能按申请日期、申请人、旅游团编号等信息进行查询 |
| 申请类 | 持久性 | 存储时间 | 永久保存，不删除，已完成的申请也需要保留历史信息 |

## 5. 统一分析类

- ☑ 类体现了系统的静态结构，通过分析类图体现软件静态结构
- ☑ 统一分析类的目的是确保每个分析类表示一个单一的明确定义的概念，而不会职责重叠
- ☑ 在分析工作完成之前，需要过滤分析类以确保创建最小数量的新概念

## 示例：统一分析类

Register for Courses  
Close Registration  
RegisterFor CoursesForm  
Course Catalog System  
Registration Controller  
Student  
Course Offering  
Schedule  
CloseRegistration Form  
Course Catalog System  
Billing System  
CloseRegistration Controller  
Student  
Course Offering  
Schedule  
RegisterFor CoursesForm  
Registration Controller  
Course Offering  
Student  
Course Catalog System  
Schedule  
CloseRegistration Controller  
CloseRegistration Form  
Billing System

## 再说分析类图

- 分析阶段的重点在于找出体现系统核心业务所需数据的实体类，而界面和业务逻辑细节分别由边界类和控制类隐藏
- 在很多UML模型中，分析阶段的工作就是找到这些实体类
- 这些实体类组成系统概念模型（分析类图）
- 通过各个用例的VOPC图，删除那些没有引用的实体类，即可得到由实体类组成的分析类图，这些是分析的关键

## 实例：旅店预订系统实体类类图

![](img/32b9da3a6e0f048e7dd2e9664c939f9e_396_0.png)

## 实例：旅游申请系统实体类类图

![](img/32b9da3a6e0f048e7dd2e9664c939f9e_397_0.png)

## UML2面向对象分析与设计

### Object-Oriented Analysis & Design with UML2

谭火彬

## 学习路线图

![](img/32b9da3a6e0f048e7dd2e9664c939f9e_399_0.png)

1. 100
2. UML
3
4
5
6. OOP / DP
7

![](img/32b9da3a6e0f048e7dd2e9664c939f9e_399_1.png)

... Case-Study ...

### 学习路线图

10...

## 第06章 面向对象的设计原则

### Object-Oriented Design Principles

## 从问题开始！

### 长方形与正方形

- ◆ 假如我们有一个类：长方形 (Rectangle)
- ◆ 我们需要一个新的类，正方形 (Square)
- ◆ 问：可否直接继承长方形？

没问题，因为数学上正方形就是长方形的子类！

## 开始设计：正方形

```java
public class Rectangle {
    private int width;
    private int height;
    public void setWidth(int w) {
        width = w;
    }
    public int getWidth() {
        return width;
    }
    public void setHeight(int h) {
        height = h;
    }
    public int getHeight() {
        return height;
    }
}
```

```java
public class Square extends Rectangle {
    public void setWidth(int w){
        super.setWidth(w);
        super.setHeight(w);
    }
    public void setHeight(int h) {
        super.setWidth(h);
        super.setHeight(h);
    }
}
```

![](img/32b9da3a6e0f048e7dd2e9664c939f9e_402_0.png)

## 设计方案正确吗？

```java
public static void resize(Rectangle r) {
    while (r.getHeight() <= r.getWidth()) {
        r.setHeight(r.getHeight() + 1);
    }
    System.out.println("It's OK.");
}
```

```java
Rectangle r1 = new Rectangle();
r1.setHeight(5);
r1.setWidth(15);
resize(r1);
```

```java
Rectangle r2 = new Square();
r2.setHeight(5);
r2.setWidth(15);
resize(r2);
```

- ✓ 使用父类（长方形）时，程序正常运行
- ✓ 使用子类（正方形）时，程序陷入死循环
- ✓ 设计出问题了？继承出问题了？

## 为什么会出现问题？

违背了面向对象的设计原则！

![](img/32b9da3a6e0f048e7dd2e9664c939f9e_404_0.png)

## 面向对象的设计原则

- ☑ 面向对象的设计原则
  - 是面向对象设计的基本指导思想
  - 是评价面向对象设计的价值观体系
  - 是设计模式的出发点和归宿

☑ 面向对象的设计原则是构造高质量软件的出发点

## 设计目标

- ☑ 构造出高质量软件，以保持系统稳定
- ☑ 设计目标
  - ◆ 可扩展性（**Extensibility**）
  - ◆ 灵活性（**Flexibility**）
  - ◆ 可插入性（**Pluggability**）
  - ◆ ……

## 设计质量：培养灵敏的嗅觉

- ☑ 糟糕的设计总是散发出臭味，让人不悦
  - ◆ 判断一个设计的好坏，主观上能否让你的合作方感到心情愉悦，是最直观的标准
- ☑ 设计开发人员要培养嗅觉，当你看到 UML 图或者代码，感到杂乱、繁琐、郁闷的时候，你可能正面对一个糟糕的设计
- ☑ 这种嗅觉是在实践开发中培养起来的，而面向对象设计原则对此加以归纳和总结

