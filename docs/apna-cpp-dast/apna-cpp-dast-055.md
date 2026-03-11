# 055：面向对象编程一站式教程

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_1.png)

在本节课中，我们将要学习C++面向对象编程的核心概念。我们将从类和对象的基础开始，逐步深入到封装、构造函数、继承、多态和抽象等高级主题。本教程旨在通过简单直白的语言和示例，帮助初学者理解这些概念，为就业面试和实际编程打下坚实基础。

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_3.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_5.png)

## 概述：什么是面向对象编程？

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_7.png)

面向对象编程是一种围绕“对象”概念构建的编程范式。对象是现实世界实体的软件表示，它包含数据（属性）和操作数据的方法（函数）。OOP的核心思想是将数据和对数据的操作封装在一起，从而提高代码的可重用性、可维护性和可扩展性。

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_9.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_10.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_12.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_14.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_16.png)

## 类和对象：蓝图与实例

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_18.png)

上一节我们介绍了面向对象编程的基本思想，本节中我们来看看其核心构件：类和对象。

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_20.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_21.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_23.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_25.png)

类是一个蓝图或模板，它定义了某一类对象共有的属性和行为。例如，“教师”这个类可以定义所有教师共有的属性（如姓名、部门、科目）和行为（如教学、评分）。

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_27.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_29.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_31.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_32.png)

对象是类的一个具体实例。根据“教师”这个蓝图，我们可以创建出许多具体的教师对象，如“张老师”、“李老师”，每个对象都有自己独特的属性值。

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_34.png)

以下是如何在C++中定义一个简单的类：

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_36.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_37.png)

```cpp
class Teacher {
    // 属性（数据成员）
    string name;
    string department;
    string subject;
    double salary;

    // 方法（成员函数）
    void teach() {
        // 教学逻辑
    }
};
```

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_39.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_40.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_41.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_43.png)

## 访问修饰符：控制可见性

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_45.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_47.png)

理解了类和对象的基本结构后，我们需要了解如何控制类成员的访问权限。这是通过访问修饰符实现的。

C++中有三个主要的访问修饰符：`private`、`public`和`protected`。
*   **private（私有）**：私有成员只能在类内部被访问。这是类的默认访问级别。
*   **public（公有）**：公有成员可以在类的外部被任何代码访问。
*   **protected（受保护）**：受保护成员与私有成员类似，但可以在派生类（子类）中被访问。

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_49.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_51.png)

访问修饰符是实现**封装**和**数据隐藏**的关键。通过将敏感数据设为私有，并通过公有的“getter”和“setter”方法来访问和修改它们，我们可以保护数据不被意外修改，并控制对数据的访问逻辑。

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_53.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_55.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_56.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_58.png)

```cpp
class Teacher {
private:
    double salary; // 私有数据，外部无法直接访问

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_60.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_62.png)

public:
    // 公有方法，用于安全地访问和修改私有数据
    void setSalary(double s) {
        if (s > 0) { // 可以添加验证逻辑
            salary = s;
        }
    }
    double getSalary() {
        return salary;
    }
};
```

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_63.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_64.png)

## 封装：捆绑数据与操作

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_66.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_68.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_69.png)

上一节我们通过访问修饰符接触了封装的思想，本节我们来详细探讨封装。

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_71.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_73.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_75.png)

封装是面向对象编程的四大支柱之一。它指的是将数据（属性）和操作这些数据的方法（函数）捆绑在一个单元（即类）中。同时，它通过访问控制（如`private`）对外部隐藏对象的内部实现细节，只暴露必要的接口。

**封装 = 数据隐藏 + 数据抽象**

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_77.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_78.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_80.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_81.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_82.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_83.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_85.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_87.png)

它就像将药物（数据）和胶囊壳（方法）包装在一起形成一个胶囊（类），外部只需要知道如何服用（调用公有方法），而无需了解内部的成分（私有数据）。

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_89.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_91.png)

```cpp
class BankAccount {
private:
    string accountId; // 隐藏内部数据
    string password;
    double balance;

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_93.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_95.png)

public:
    // 暴露安全的操作接口
    bool withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
            return true;
        }
        return false;
    }
    double checkBalance() {
        return balance;
    }
};
```

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_97.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_99.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_101.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_102.png)

## 构造函数与析构函数：对象的生与死

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_104.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_106.png)

当我们创建对象时，经常需要初始化其属性。C++使用一种特殊的成员函数来自动完成初始化工作，这就是构造函数。

构造函数是一种特殊的成员函数，它在创建类的新对象时**自动调用**。它的名称与类名完全相同，并且没有返回类型。

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_108.png)

```cpp
class Teacher {
public:
    string name;
    string department;

    // 构造函数
    Teacher() {
        cout << "构造函数被调用！" << endl;
        department = "计算机科学"; // 初始化部门
    }
};

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_110.png)

int main() {
    Teacher t1; // 创建对象时，构造函数自动执行
    cout << t1.department << endl; // 输出：计算机科学
    return 0;
}
```

构造函数主要有三种类型：
1.  **默认构造函数**：没有参数。
2.  **参数化构造函数**：带有参数，用于用特定值初始化对象。
3.  **拷贝构造函数**：用于用一个已存在的对象初始化一个新对象。

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_112.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_114.png)

与构造函数对应的是**析构函数**。它在对象销毁时自动调用，用于执行清理工作（如释放动态分配的内存）。析构函数的名称是在类名前加一个波浪号`~`。

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_116.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_118.png)

```cpp
class Teacher {
public:
    // 构造函数
    Teacher() {
        cout << "对象诞生" << endl;
    }
    // 析构函数
    ~Teacher() {
        cout << "对象销毁" << endl;
    }
};
```

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_120.png)

## 深拷贝与浅拷贝

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_122.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_123.png)

在使用拷贝构造函数或赋值操作时，理解深拷贝和浅拷贝至关重要，尤其是在类包含指针成员时。

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_125.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_126.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_127.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_129.png)

*   **浅拷贝**：只拷贝指针的值（即内存地址），使得两个对象中的指针指向同一块内存。修改一个对象的数据会影响另一个对象。
*   **深拷贝**：为新对象分配新的内存空间，并拷贝原指针指向的实际数据。这样两个对象就拥有独立的数据副本。

```cpp
class Student {
public:
    char *name;
    // 构造函数
    Student(const char *n) {
        name = new char[strlen(n) + 1];
        strcpy(name, n);
    }
    // 自定义深拷贝构造函数
    Student(const Student &other) {
        name = new char[strlen(other.name) + 1]; // 分配新内存
        strcpy(name, other.name); // 拷贝数据
    }
    // 析构函数
    ~Student() {
        delete[] name; // 释放内存
    }
};
```

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_131.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_133.png)

## 继承：代码的重用与扩展

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_135.png)

继承是面向对象编程中实现代码重用的强大机制。它允许我们基于一个已有的类（基类或父类）来定义一个新类（派生类或子类）。派生类继承了父类的属性和方法，并可以添加自己特有的属性和方法。

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_137.png)

```cpp
// 基类（父类）
class Person {
public:
    string name;
    int age;
};
// 派生类（子类）
class Student : public Person { // ‘public’ 表示继承方式
public:
    int rollNumber;
};

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_139.png)

int main() {
    Student s1;
    s1.name = "小明"; // 继承自Person的属性
    s1.rollNumber = 123; // Student自己的属性
    return 0;
}
```

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_141.png)

继承有多种类型：
*   **单继承**：一个子类只继承一个父类。
*   **多级继承**：类A被类B继承，类B又被类C继承。
*   **多重继承**：一个子类继承多个父类。
*   **层次继承**：一个父类被多个子类继承。
*   **混合继承**：以上几种继承类型的组合。

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_143.png)

## 多态：同一接口，多种实现

多态是面向对象编程的另一个核心概念，意为“多种形态”。它允许我们使用统一的接口来操作不同的底层对象。多态主要通过函数重载、运算符重载、函数重写和虚函数实现。

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_145.png)

多态分为两类：
1.  **编译时多态（静态多态）**：在编译时确定调用哪个函数。例如：
    *   **函数重载**：在同一作用域内，函数名相同但参数列表不同。
    ```cpp
    class Print {
    public:
        void show(int i) { cout << "整数: " << i << endl; }
        void show(char c) { cout << "字符: " << c << endl; } // 重载
    };
    ```
    *   **运算符重载**
2.  **运行时多态（动态多态）**：在程序运行时确定调用哪个函数。主要通过**虚函数**和**函数重写**实现。
    ```cpp
    class Animal { // 基类
    public:
        virtual void speak() { // 虚函数
            cout << "动物叫" << endl;
        }
    };
    class Dog : public Animal {
    public:
        void speak() override { // 重写基类虚函数
            cout << "汪汪！" << endl;
        }
    };

    int main() {
        Animal *a = new Dog();
        a->speak(); // 输出“汪汪！”，调用的是Dog类的speak
        delete a;
        return 0;
    }
    ```

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_147.png)

## 抽象：隐藏复杂性

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_149.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_150.png)

抽象是隐藏不必要的实现细节，只向用户展示核心功能的过程。在C++中，抽象主要通过：
1.  **访问修饰符**（如将细节设为`private`）。
2.  **抽象类**来实现。

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_152.png)

抽象类是不能被实例化（即不能创建对象）的类，它通常包含至少一个**纯虚函数**。抽象类作为接口或蓝图，供其他类继承并实现其纯虚函数。

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_154.png)

```cpp
// 抽象类
class Shape {
public:
    virtual void draw() = 0; // 纯虚函数
};
// 具体类
class Circle : public Shape {
public:
    void draw() override {
        cout << "绘制圆形" << endl; // 实现纯虚函数
    }
};

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_156.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_158.png)

int main() {
    // Shape s; // 错误！不能创建抽象类的对象
    Circle c;
    c.draw(); // 正确
    return 0;
}
```

## 静态成员：属于类而非对象

静态成员（变量或函数）属于类本身，而不是类的某个特定对象。所有对象共享同一个静态成员副本。

*   **静态变量**：在程序生命周期内只初始化一次，所有对象共享其值。
*   **静态函数**：只能访问静态成员，不能访问非静态成员（因为没有`this`指针）。

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_160.png)

```cpp
class Counter {
public:
    static int count; // 静态变量声明

    Counter() {
        count++; // 每个对象创建时，共享的count加1
    }
    static void showCount() { // 静态函数
        cout << "对象总数: " << count << endl;
    }
};
int Counter::count = 0; // 静态变量定义和初始化

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_162.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_164.png)

int main() {
    Counter c1, c2, c3;
    Counter::showCount(); // 输出：对象总数: 3
    return 0;
}
```

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_166.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_168.png)

## 总结

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_170.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_172.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_174.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_176.png)

本节课中我们一起学习了C++面向对象编程的核心概念。我们从**类和对象**这一基础开始，理解了类是蓝图，对象是实例。接着，我们探讨了**访问修饰符**（`private`, `public`, `protected`）如何控制封装性。

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_178.png)

**封装**将数据和方法捆绑并隐藏细节。**构造函数和析构函数**管理对象的生命周期。**深拷贝与浅拷贝**在处理指针成员时尤为重要。

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_180.png)

**继承**实现了代码的层次化重用，而**多态**（包括编译时和运行时）则提供了接口的一致性。**抽象**通过抽象类和纯虚函数定义了清晰的接口。最后，**静态成员**提供了类级别的数据和函数。

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_182.png)

![](img/489e2eadd5da3b1b0c0c78249ff6c8ec_184.png)

掌握这些概念是理解现代C++编程和应对技术面试的关键。建议通过实际编码练习来巩固这些知识。