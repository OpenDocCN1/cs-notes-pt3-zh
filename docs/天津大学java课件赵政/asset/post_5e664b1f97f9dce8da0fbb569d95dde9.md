
## 重载（overload）

### 例 P148下

```java
// Methods with differing type signatures are overloaded – not
// overridden.
class A {
    int i, j;
    A(int a, int b) {
        i = a;
        j = b;
    }
    // display i and j
    void show() {
        System.out.println("i and j: " + i + " " + j);
    }
}

// Create a subclass by extending class A.
class B extends A {
    int k;
    B(int a, int b, int c) {
        super(a, b);
        k = c;
    }

    // overload show()
    void show(String msg) {
        System.out.println(msg + k);
    }
}

class Overload {
    public static void main(String args[]) {
        B subOb = new B(1, 2, 3);
        subOb.show("This is k: "); // this calls show() in B
        subOb.show(); // this calls show() in A
    }
}
```

### Ans:

```text
This is k: 3
i and j: 1 2
```

## 8.6 动态方法调度（dynamic method dispatch）

- 一种在运行时而不是编译时调用重写方法的机制。
- 是 Java 实现运行时多态性的基础。
- 超类的引用变量可以引用子类对象。
- Java 根据当前被引用对象的类型来决定执行哪个版本的方法。
- Java 中的重写方法与 C++ 中的虚函数类似。

### 例 P150

```java
// Dynamic Method Dispatch
class A {
    void callme() {
        System.out.println("Inside A's callme method");
    }
}

class B extends A {
    void callme() {    // override callme()
        System.out.println("Inside B's callme method");
    }
}

class C extends A {
    void callme() {    // override callme()
        System.out.println("Inside C's callme method");
    }
}

class Dispatch {
    public static void main(String args[]) {
        A a = new A(); // object of type A
        B b = new B(); // object of type B
        C c = new C(); // object of type C
        A r;
        // obtain a reference of type A
        r = a; // r refers to an A object
        r.callme(); // calls A's version of callme
        r = b; // r refers to a B object
        r.callme(); // calls B's version of callme
        r = c; // r refers to a C object
        r.callme(); // calls C's version of callme
    }
}
```

### Ans:

- Inside A's callme method
- Inside B's callme method
- Inside C's callme method

![](img/489adce8323ca3a7b0e9fe701e6e665c_385_0.png)

### 8.6.1 为什么要重写方法

- 重写方法允许 Java 支持运行时多态性。
- 允许通用类指定方法，且对所有派生类都是公用的。同时该方法允许子类定义这些方法中的某些或全部的特殊实现。
- 实现多态性——“一个接口，多个方法”的另一种方式。
- 超类提供子类可以直接运用的所有元素。多态也定义了这些派生类必须自己实现的方法。
- 通过继承和重写方法的联合，超类可以定义供它的所有子类使用的方法的通用形式。

### 8.6.2 应用方法重写

- 通过继承和运行时多态的双重机制，可以定义一个被很多不同却有关的对象类型运用的一致的接口。

### 例 P151

```java
// Using run-time polymorphism.
class Figure {
    double dim1;
    double dim2;
    Figure(double a, double b) {
        dim1 = a;
        dim2 = b;
    }
    double area() {
        System.out.println("Area for Figure is undefined.");
        return 0;
    }
}
```

```java
class FindAreas {
    public static void main(String args[]) {
        Figure f = new Figure(10, 10);
        Rectangle r = new Rectangle(9, 5);
        Triangle t = new Triangle(10, 8);
        Figure figref;
        figref = r;
        System.out.println("Area is " + figref.area());
        figref = t;
        System.out.println("Area is " + figref.area());
        figref = f;
        System.out.println("Area is " + figref.area());
    }
}
```

### Ans:

```text
Inside Area for Rectangle.
Area is 45

Inside Area for Triangle.
Area is 40

Area for Figure is undefined.
Area is 0
```

![](img/489adce8323ca3a7b0e9fe701e6e665c_391_0.png)

## 8.7 使用抽象类

- 定义一个超类，该超类定义了一种给定结构的抽象，但不提供任何完整的方法实现。
- 创建一个只定义一个被它的所有子类共享的通用形式，由每个子类自己去填写细节。
- 为了确保子类真正重写所有必需的方法，Java 使用抽象方法（abstract method）。
- 声明一个抽象方法，通用形式：（不存在方法体）

  ```java
  abstract type name(parameter-list);
  ```

- 抽象类没有对象，一个抽象类不能通过 new 操作符直接实例化。
- 抽象类的子类必须实现超类中的所有抽象方法，或者自己也声明成 `abstract`。

### 例 P153 抽象方法类，该类后面是实现抽象方法的类

```java
// A simple demonstration of abstract.
abstract class A {
    abstract void callme();
    // concrete methods are still allowed in abstract classes
    void callmetoo() {
        System.out.println("This is a concrete method.");
    }
}

class B extends A {
    void callme() {
        System.out.println("B's implementation of callme.");
    }
}

class AbstractDemo {
    public static void main(String args[]) {
        B b = new B();
        b.callme();
        b.callmetoo();
    }
}
```
