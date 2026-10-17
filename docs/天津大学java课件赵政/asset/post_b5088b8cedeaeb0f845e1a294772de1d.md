

## 6.1 类基础

- 类的最重要的事情就是它定义了一种新的数据类型。
- 定义后，就可以用这种新类型来创建该类型的对象。
- 类就是对象的模板（template），而对象就是类的一个实例（instance）。

### 6.1.1 类的通用格式

- 可以通过指定它包含的数据和操作数据的代码来定义类。
- 类的代码定义了该类数据的接口。
- 类定义的通用格式如下所示：

```java
class classname {
    type instance-variable1;    // 数据或变量被称为实例变量
    // ...
    type instance-variableN;
    type methodname1(parameter-list) {    // 代码包含在方法内

    // body of method
    }
    // ...
    Type methodnameN(parameter-list) {
    // body of method
    }
}
```

### 6.1.2 一个简单的类

- 定义了一个名为 Box 的类，它定义了3个实例变量，不包含任何方法：

```java
class Box {
    double width;
    double height;
    double depth;
}
```

- 创建一个 Box 对象：

```java
// create a Box object called mybox
Box mybox = new Box();
```

- 该对象包含它自己的由类定义的每个实例变量的拷贝。
- 使用点号 “.” 运算符访问这些变量：

```java
mybox.width = 100;
```

### 例 P92上 Box 类的完整程序

```java
/* A program that uses the Box class.
Call this file BoxDemo.java
*/
class Box {
    double width; double height; double depth;
}
// This class declares an object of type Box.
class BoxDemo {
    public static void main(String args[]) {
        Box mybox = new Box();
        double vol;
        // assign values to mybox's instance variables
        mybox.width = 10;
        mybox.height = 20;
        mybox.depth = 15;
        // compute volume of box
        vol = mybox.width * mybox.height * mybox.depth;
        System.out.println("Volume is " + vol);
    }
}
```

Ans:

Volume is 3000.0

### 例 P92下 两个 Box 对象

```java
// This program declares two Box objects.
class Box {
    double width;
    double height;
    double depth;
}
class BoxDemo2 {
    public static void main(String args[]) {
        Box mybox1 = new Box();
        Box mybox2 = new Box();
        double vol;

        // assign values to mybox1's instance variables
        mybox1.width = 10;
        mybox1.height = 20;
        mybox1.depth = 15;
        /* assign different values to mybox2's
           instance variables */
        mybox2.width = 3;
        mybox2.height = 6;
        mybox2.depth = 9;
        // compute volume of first box
        vol = mybox1.width * mybox1.height * mybox1.depth;
        System.out.println("Volume is " + vol);
        // compute volume of second box
        vol = mybox2.width * mybox2.height * mybox2.depth;
        System.out.println("Volume is " + vol);
    }
}
```

![](img/489adce8323ca3a7b0e9fe701e6e665c_235_0.png)

Ans:

Volume is 3000.0

Volume is 162.0

/* 改变一个对象的实例变量对另外一个对象的实例变量没有任何影响，mybox1 的数据与 mybox2 的数据完全分离。 */

## 6.2 声明对象

- 用下面的语句来声明一个 Box 类型的对象：

```java
Box mybox = new Box();
```

- 改写为下面的形式：

```java
Box mybox; // declare reference to object
mybox = new Box(); // allocate a Box object
```

- 效果如图：

![](img/489adce8323ca3a7b0e9fe701e6e665c_238_0.png)

### 6.2.1 深入研究 new 运算符

- new 运算符的通用格式如下：

```java
class-var = new classname();
```

- class-var 是所创建类类型的变量（对象名）。
- classname 是被实例化的类的名字。
- （）指定了类的构造函数。
- 简单类型不是作为对象实现的，所以不使用 new 运算符。
- new 有可能由于内存不足而无法给一个对象分配内存。就会发生运行时异常。

## 6.3 给对象引用变量赋值

- 对象变量的赋值：

```java
Box b1 = new Box();
Box b2 = b1;
```

- 对象变量的赋值将引用同样的对象。
- 没有分配任何内存或对原对象做任何部分的拷贝。它们是同一个对象。如图所示。
- 脱离（unhook）初始对象：

```java
Box b1 = new Box();
Box b2 = b1;
// ...
b1 = null;
```

![](img/489adce8323ca3a7b0e9fe701e6e665c_240_0.png)

## 6.4 方法

- 方法一般的形式：

```java
type name(parameter-list) {
    // body of method
}
```

- Type: 方法返回的数据类型。可以是任何合法有效的类型，包括你创建的类的类型。
- 如果该方法不返回任何值，则它的返回值 type 必须为 void。
- 方法名由 name 指定。除了被当前作用域中的其他项使用的标识符以外，方法名可以是任何合法的标识符。
- 自变量列表：是一系列类型和标识符对，用逗号分开。如果方法没有自变量，那么自变量列表就为空。
- 对于不返回 void 类型的方法，使用下面格式的 return 语句，方法返回值到它的调用程序：

```java
return value;
```

### 6.4.1 为 Box 类添加一个方法

- 当一个实例变量不是被该实例变量所在类的部分代码访问时，它必须通过该对象加点运算符来访问。
- 但是当一个实例变量被定义该变量的类的代码访问时，该变量可以被直接引用。

```java
class BoxDemo3 {
    public static void main(String args[]) {
        Box mybox1 = new Box();
        Box mybox2 = new Box();
        // assign values to mybox1's instance variables
        mybox1.width = 10;
        mybox1.height = 20;
        mybox1.depth = 15;
        /* assign different values to mybox2's
           instance variables */
        mybox2.width = 3;
        mybox2.height = 6;
        mybox2.depth = 9;
        // display volume of first box
        mybox1.volume();
        // display volume of second box
        mybox2.volume();
    }
}
```

![](img/489adce8323ca3a7b0e9fe701e6e665c_244_0.png)

