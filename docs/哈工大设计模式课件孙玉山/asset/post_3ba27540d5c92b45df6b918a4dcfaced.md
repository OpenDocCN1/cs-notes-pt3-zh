
## Class Relations (类间关系)

- **Association relation (关联关系)**
  - An association between two classes represents a collaboration between the classes or their corresponding instances.
  - Association relation includes:
    - **Aggregation relation (聚合关系)**：类B以一个实例化对象的形式作为A的一个属性 ![](img/95717dc23f76db2057b9aa0c49790307_124_0.png)
    - **Dependency relation (依赖关系)**：表现为类B作为参数被类A某个方法使用 ![](img/95717dc23f76db2057b9aa0c49790307_124_1.png)
  - In Java language, association relation can be realized by instance variables. ![](img/95717dc23f76db2057b9aa0c49790307_125_0.png)

- **Aggregation relation (聚合关系)** is one kind of association relationship. It is a stronger type of association.
  - This relation expresses a relationship of a whole and a part.
  - An aggregation has a hollow diamond end pointing to the part containing the whole. ![](img/95717dc23f76db2057b9aa0c49790307_127_0.png)

- **关联关系与聚合关系的区别：**
  - Like association, aggregation is realized by instance variables. But the difference is that:
    - **In an association relationship**, the classes being associated are in the same level.
    - **In an aggregation relationship**, the classes being associated are in different levels, one represents the whole and the other represents the part.

- **Dependency relation (依赖关系)**
  - Dependency relation is a relation in which one class is dependent on another class.
  - One person can buy a car and house and so Person class is dependent on Car and House classes.
  - Use dotted lines to represent dependency relation.
  - 通过参数，达到关联 ![](img/95717dc23f76db2057b9aa0c49790307_130_0.png)
  - Different from association, Person class has no attributes of class Car and House.
  - The object of Car and House is passed into class Person by using parameter in `buy(Car car)` and `buy(House house)`.
  - Example of dependency relation

## Java Abstract Class

### Characteristics of Abstract Classes

```
SortStrategy
-algorithmName: String
#showInfo(): void
+sort(a: int[]): void;
```

US cars

### Form of an Abstract Class

```
abstract public class SortStrategy {
    private String algorithmName = "";  //private variable

    public SortStrategy() {
        // code omitted
    }
    protected void showInfo(){
        // concrete function
        System.out.println("sort integers");
    }
    public abstract void sort(int[] a); //abstract function
}
```

### Characteristics of Abstract Classes

- Abstract class provides only partial implementation of a type. (What this means?)
- Abstract class can have
  - Private variables (私有变量)
  - Constructors (be called by subclasses) (构造函数)
  - abstract methods (be implemented by subclasses) (抽象方法)
  - Concrete methods (be called by subclasses directly) (已实现方法)
- Abstract classes can not be used by clients to create objects
- Thus, if you want to use an abstract class with its subclasses, you need to create an object of one of the subclasses. Then you can use this object to call the methods both in the subclass or the superclass (Question: What kinds of methods can be called?)

### How to use Abstract classes?

![](img/95717dc23f76db2057b9aa0c49790307_136_0.png)

US cars

- 1) Use an abstract class by claiming a variable of the abstract class type and create objects of its subclasses and then call the methods in the subclasses

```
USCar myCar;
//...
if(condition1==true)
    myCar = new Lincoln();
else if(condition2==true)
    myCar = new Buick();

myCar.getInstructions()
```

### Abstract Class and Inheritance

- 2) use an abstract class by inheriting it
  - a) Use abstract class as super class and the subclasses can use some concrete functionalities of the super class.
  - b) Different subclasses may have different implementations of the abstract methods of the super class
