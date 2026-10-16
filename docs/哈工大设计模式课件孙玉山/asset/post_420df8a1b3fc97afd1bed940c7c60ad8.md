
## Introduction to Factory Method Pattern

### Functionalities of the factory method (工厂方法的功能)

- Thus, a factory method can be defined as a method in a class that:
  - 选择一个类：Selects an appropriate class from a class hierarchy based on the application context and other influencing factors
  - 创建该类的对象：Instantiates the selected class and
  - 以超类的类型返回该对象：returns it as an instance of the parent class type

### Advantages of the factory method (工厂方法的优点)

1. Clean Client program (干净的客户端程序)

   Application objects can make use of the factory method to get access to the appropriate class instance. This eliminates the need for an application object to deal with the varying class selection criteria.

2. Hide details in instantiating an object (隐藏实例化对象时的细节)

   The factory method also implements any special mechanisms required to instantiate the selected class.

   - This is possible **when different classes in the hierarchy need to be instantiated in different ways**. The factory method hides these details from application objects and eliminates the need for them to deal with these intricacies.

3. Client doesn’t need to know which concrete class has been instantiated (客户类只需要知道哪种类型的对象被创建了，而不必知道哪个具体的子类被实例化了)

   Because the factory method returns the selected class instance as an object of the parent class type, a client program does not have to be aware of the existence of the classes in the hierarchy.

## 以下给出两种不同的工厂方法模式

- 简单工厂方法模式
- 工厂方法模式

## Theory of the Simple Factory Method Pattern and Design Examples

### The Simple Factory Method Pattern

**工厂类：**

- 静态方法
- 没有子类

Diagram of Simple Factory Pattern:

![](img/95717dc23f76db2057b9aa0c49790307_254_0.png)

### Creator (工厂类)

- 中心：the center of the factory pattern
- 包含业务逻辑：Contains business logic that application needs
- 创建产品类对象：Factory method creates an object of Product type when called by the client program, and returns this object to the caller object

**Product：**

- Java interface or abstract Java class
- Common interface or super class for the concrete subclasses

**Concrete Products：**

- Concrete Java classes to implement interface `Product` or to extend abstract class `Product`

**Simple Factory Pattern Implementation:**

```text
Client
Product
可以传递参数给工厂类
Creator.factory(p)
Creator
+factory()
Product1
Product2
Product12
Product21
Product22
Product211
Product212
仅仅负责创建对象
```

### Example of Auto Insurance Policies (汽车保险的例子——简单工厂方法模式)

![](img/95717dc23f76db2057b9aa0c49790307_258_0.png)

- The following class diagram represents a design using factory method pattern to query about the features of different types of auto insurances.
- **AutoInsurance:** interface to claim various insurance policies (here `describe()`)
- Four subclasses implement the interface `AutoInsurance`:
  - **Body**: Bodily Injury Liability (人身保险，你撞了别人)
  - **Collision**: Collision Coverage (车碰撞险，你的车损坏了)
  - **Com**: Comprehensive Coverage (综合险)
  - **Person**: Personal Injury Protection (驾驶员保险)
- **PolicyProducer** is a factory class with a factory method:
  `getPolicyObj(String option)`
  which will create and return an object of `AutoInsurance` type.
- Actually, it will create and return an object of one of the implementing classes according to the chosen parameter `option` entered.

**Source Code**

```java
public interface AutoInsurance {
    abstract String describe();
}
```

```java
public class Body implements AutoInsurance {
    private String description;

    public String describe() {
        description = "Bodily Injury Liability";
        return description;
    }
}
```
