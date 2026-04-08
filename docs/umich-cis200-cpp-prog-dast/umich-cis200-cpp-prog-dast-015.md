# 015：继承与多态 🧬

![](img/67b299d44f971e497bba75eb16b39af6_0.png)

![](img/67b299d44f971e497bba75eb16b39af6_2.png)

![](img/67b299d44f971e497bba75eb16b39af6_4.png)

在本节课中，我们将学习面向对象编程中的两个核心概念：**继承**和**多态**。我们将通过构建一个简单的“战斗宠物”游戏类结构来实践动态内存管理，然后深入探讨如何通过继承创建类层次结构，并利用多态实现运行时行为绑定。

![](img/67b299d44f971e497bba75eb16b39af6_6.png)

![](img/67b299d44f971e497bba75eb16b39af6_8.png)

![](img/67b299d44f971e497bba75eb16b39af6_10.png)

![](img/67b299d44f971e497bba75eb16b39af6_12.png)

![](img/67b299d44f971e497bba75eb16b39af6_13.png)

---

## 项目回顾与动态内存管理 🧠

![](img/67b299d44f971e497bba75eb16b39af6_15.png)

![](img/67b299d44f971e497bba75eb16b39af6_17.png)

上一节我们介绍了动态内存管理和“大三法则”（析构函数、拷贝构造函数、拷贝赋值运算符）。本节中，我们来看看如何在一个具体的项目中应用这些规则。

![](img/67b299d44f971e497bba75eb16b39af6_19.png)

![](img/67b299d44f971e497bba75eb16b39af6_21.png)

![](img/67b299d44f971e497bba75eb16b39af6_23.png)

![](img/67b299d44f971e497bba75eb16b39af6_25.png)

![](img/67b299d44f971e497bba75eb16b39af6_27.png)

![](img/67b299d44f971e497bba75eb16b39af6_28.png)

![](img/67b299d44f971e497bba75eb16b39af6_30.png)

以下是我们在`Trainer`类中实现动态数组管理的核心代码片段：

![](img/67b299d44f971e497bba75eb16b39af6_32.png)

![](img/67b299d44f971e497bba75eb16b39af6_34.png)

![](img/67b299d44f971e497bba75eb16b39af6_36.png)

![](img/67b299d44f971e497bba75eb16b39af6_38.png)

![](img/67b299d44f971e497bba75eb16b39af6_39.png)

```cpp
// 析构函数：释放动态数组
Trainer::~Trainer() {
    delete[] fightingPets;
}

![](img/67b299d44f971e497bba75eb16b39af6_40.png)

![](img/67b299d44f971e497bba75eb16b39af6_42.png)

// 拷贝构造函数：深拷贝
Trainer::Trainer(const Trainer& other) {
    name = other.name;
    level = other.level;
    experiencePoints = other.experiencePoints;
    maxNumFightingPets = other.maxNumFightingPets;
    currentNumFightingPets = other.currentNumFightingPets;

    // 分配新内存并复制内容
    fightingPets = new FightingPet[maxNumFightingPets];
    for (int i = 0; i < currentNumFightingPets; ++i) {
        fightingPets[i] = other.fightingPets[i];
    }
}

![](img/67b299d44f971e497bba75eb16b39af6_44.png)

![](img/67b299d44f971e497bba75eb16b39af6_46.png)

// 拷贝赋值运算符
Trainer& Trainer::operator=(const Trainer& other) {
    if (this != &other) { // 防止自赋值
        // 1. 释放原有内存
        delete[] fightingPets;

        // 2. 复制基本成员
        name = other.name;
        level = other.level;
        experiencePoints = other.experiencePoints;
        maxNumFightingPets = other.maxNumFightingPets;
        currentNumFightingPets = other.currentNumFightingPets;

        // 3. 分配新内存并深拷贝数组
        fightingPets = new FightingPet[maxNumFightingPets];
        for (int i = 0; i < currentNumFightingPets; ++i) {
            fightingPets[i] = other.fightingPets[i];
        }
    }
    return *this;
}
```

通过这个练习，我们确保了每个`Trainer`对象都拥有自己独立的战斗宠物数组，避免了浅拷贝可能导致的多个对象共享同一块内存的问题。

![](img/67b299d44f971e497bba75eb16b39af6_48.png)

![](img/67b299d44f971e497bba75eb16b39af6_50.png)

---

## 继承基础：建立“是一个”关系 🏗️

理解了如何管理类内部的资源后，我们来看看如何通过继承来建立类之间的关系。继承允许我们创建一个新类（派生类），它基于一个已存在的类（基类），并可以添加或修改功能。

![](img/67b299d44f971e497bba75eb16b39af6_52.png)

我们从一个简单的`Rectangle`类开始：

![](img/67b299d44f971e497bba75eb16b39af6_54.png)

![](img/67b299d44f971e497bba75eb16b39af6_56.png)

![](img/67b299d44f971e497bba75eb16b39af6_58.png)

```cpp
class Rectangle {
private:
    int height;
    int width;
public:
    Rectangle(int h, int w) : height(h), width(w) {}
    int getHeight() const { return height; }
    int getWidth() const { return width; }
    int getArea() const { return height * width; }
    int getPerimeter() const { return 2 * (height + width); }

    // 标记为 virtual，允许在派生类中被覆盖
    virtual void setHeight(int h) {
        if (h < 0) throw std::invalid_argument("Height cannot be negative");
        height = h;
    }
    virtual void setWidth(int w) {
        if (w < 0) throw std::invalid_argument("Width cannot be negative");
        width = w;
    }
};
```

现在，我们创建一个`Square`类。在几何上，正方形是一种特殊的矩形，因此“正方形是一个矩形”的关系成立，适合使用继承。

```cpp
// Square 公有继承自 Rectangle
class Square : public Rectangle {
public:
    // 正方形只需要一个边长参数
    Square(int side) : Rectangle(side, side) {}

    // 覆盖基类的设置函数，确保正方形属性不变
    void setHeight(int h) override {
        // 调用基类的两个设置函数，保持长宽相等
        Rectangle::setHeight(h);
        Rectangle::setWidth(h);
    }

    void setWidth(int w) override {
        // 调用基类的两个设置函数，保持长宽相等
        Rectangle::setWidth(w);
        Rectangle::setHeight(w);
    }
};
```

关键点在于：
1.  `: public Rectangle` 表示公有继承。
2.  构造函数通过初始化列表调用基类构造函数。
3.  `override` 关键字明确表示此函数旨在覆盖基类的虚函数，有助于编译器检查错误。

![](img/67b299d44f971e497bba75eb16b39af6_60.png)

---

![](img/67b299d44f971e497bba75eb16b39af6_62.png)

![](img/67b299d44f971e497bba75eb16b39af6_64.png)

![](img/67b299d44f971e497bba75eb16b39af6_66.png)

![](img/67b299d44f971e497bba75eb16b39af6_68.png)

## 多态性：运行时魔法 ✨

![](img/67b299d44f971e497bba75eb16b39af6_70.png)

![](img/67b299d44f971e497bba75eb16b39af6_72.png)

![](img/67b299d44f971e497bba75eb16b39af6_74.png)

多态性允许我们使用基类的指针或引用来调用派生类的方法。这是面向对象编程最强大的特性之一，但它需要与**指针**和**虚函数**配合使用才能实现运行时绑定。

![](img/67b299d44f971e497bba75eb16b39af6_76.png)

![](img/67b299d44f971e497bba75eb16b39af6_77.png)

![](img/67b299d44f971e497bba75eb16b39af6_78.png)

以下是展示多态性的示例：

![](img/67b299d44f971e497bba75eb16b39af6_80.png)

```cpp
void printShapeDetails(Rectangle* shapePtr) {
    std::cout << "Area: " << shapePtr->getArea() << std::endl;
    std::cout << "Perimeter: " << shapePtr->getPerimeter() << std::endl;
}

int main() {
    // 使用指针和堆内存
    Rectangle* rectPtr = new Rectangle(10, 20);
    Square* squarePtr = new Square(5);

    // 多态调用：相同的接口，不同的行为
    printShapeDetails(rectPtr);   // 调用 Rectangle 的 getArea 和 getPerimeter
    printShapeDetails(squarePtr); // 调用 Square 的 getArea 和 getPerimeter
    // 尽管 printShapeDetails 接收的是 Rectangle 指针，
    // 但传入 Square 指针时，会正确调用 Square 类的方法。

    // 演示虚函数覆盖的效果
    squarePtr->setWidth(1); // 由于覆盖，这会同时改变长和宽
    printShapeDetails(squarePtr); // 面积变为 1， 周长变为 4

    delete rectPtr;
    delete squarePtr;
    return 0;
}
```

**核心机制**：
*   当通过基类指针调用一个**虚函数**时，C++会在运行时查找对象的实际类型，并调用该类型对应的函数版本。
*   这就是为什么`squarePtr`被当作`Rectangle*`传入后，仍然能正确调用`Square`类中覆盖的`setWidth`和`getArea`方法。
*   如果没有`virtual`关键字，编译器将在编译时根据指针类型决定调用哪个函数（静态绑定），从而无法实现多态。

---

![](img/67b299d44f971e497bba75eb16b39af6_82.png)

![](img/67b299d44f971e497bba75eb16b39af6_84.png)

![](img/67b299d44f971e497bba75eb16b39af6_86.png)

## 项目一预告：游戏单位类层次 🎮

![](img/67b299d44f971e497bba75eb16b39af6_88.png)

![](img/67b299d44f971e497bba75eb16b39af6_90.png)

在接下来的项目中，我们将运用继承和多态来构建一个简单游戏的类结构。

![](img/67b299d44f971e497bba75eb16b39af6_92.png)

![](img/67b299d44f971e497bba75eb16b39af6_94.png)

![](img/67b299d44f971e497bba75eb16b39af6_96.png)

![](img/67b299d44f971e497bba75eb16b39af6_98.png)

以下是主要的类设计概述：

![](img/67b299d44f971e497bba75eb16b39af6_100.png)

![](img/67b299d44f971e497bba75eb16b39af6_101.png)

![](img/67b299d44f971e497bba75eb16b39af6_103.png)

![](img/67b299d44f971e497bba75eb16b39af6_105.png)

1.  **基类：`Unit`（单位）**
    *   所有游戏单位的基类。
    *   **属性**：攻击力、生命值、位置（x, y）、所属队伍。
    *   **虚函数**：`attack(Unit* target)`, `move(...)`。
    *   攻击逻辑需要计算距离并判断队伍关系。

![](img/67b299d44f971e497bba75eb16b39af6_107.png)

![](img/67b299d44f971e497bba75eb16b39af6_109.png)

![](img/67b299d44f971e497bba75eb16b39af6_111.png)

![](img/67b299d44f971e497bba75eb16b39af6_113.png)

![](img/67b299d44f971e497bba75eb16b39af6_115.png)

2.  **派生类1：`Infantry`（步兵）**
    *   继承自`Unit`。
    *   固定属性：攻击力5，生命值10。
    *   移动方式：每次沿X或Y轴移动最多5个单位。

![](img/67b299d44f971e497bba75eb16b39af6_117.png)

![](img/67b299d44f971e497bba75eb16b39af6_119.png)

3.  **派生类2：`Artillery`（炮兵）**
    *   继承自`Unit`。
    *   固定属性：攻击力10，生命值1，射程更长。
    *   移动方式：缓慢，每次移动1个单位。

![](img/67b299d44f971e497bba75eb16b39af6_121.png)

![](img/67b299d44f971e497bba75eb16b39af6_123.png)

![](img/67b299d44f971e497bba75eb16b39af6_125.png)

4.  **派生类3：`Cavalry`（骑兵）**
    *   继承自`Unit`。
    *   固定属性：攻击力5，生命值10，射程5。
    *   移动方式：快速，每次移动10个单位。

![](img/67b299d44f971e497bba75eb16b39af6_127.png)

5.  **多级继承：`Captain`（上尉）**
    *   继承自`Infantry`（因此也间接继承自`Unit`）。
    *   特殊能力：覆盖`attack`函数，攻击时还能“鼓舞”友军单位，为其恢复全部生命值。

![](img/67b299d44f971e497bba75eb16b39af6_129.png)

这个结构充分利用了继承（`Captain` `is an` `Infantry`， `Infantry` `is a` `Unit`）和多态（通过`Unit*`指针管理所有不同类型单位，并调用其特定的`attack`和`move`行为）。

---

## 总结与最佳实践 📚

本节课中我们一起学习了：
1.  **继承**：用于建立“是一个”关系，实现代码复用和层次化类设计。使用 `class Derived : public Base` 语法。
2.  **多态**：与虚函数和指针结合，实现“一个接口，多种实现”的运行时行为。这是设计灵活、可扩展系统的关键。
3.  **关键语法**：
    *   基类函数前加 `virtual`。
    *   派生类覆盖函数后加 `override`。
    *   通过基类指针或引用来操作派生类对象。
4.  **设计提示**：不要滥用继承。只有当两个类之间确实存在严格的“是一个”关系时才使用继承（如“正方形是一个矩形”）。对于“有一个”关系（如“训练师有战斗宠物”），应使用组合（将对象作为成员变量）。

![](img/67b299d44f971e497bba75eb16b39af6_131.png)

记住，管理好动态内存（大三法则）是构建稳健类的基础，而继承和多态则是构建复杂、可维护系统架构的强大工具。在接下来的实验和项目中，请积极应用这些概念。