# C语言编程与计算机底层原理：第5讲：结构体 🏗️

在本节课中，我们将要学习C语言中的结构体。结构体是一种复合数据类型，允许我们将不同类型的数据组合在一起。我们将学习如何定义结构体、创建结构体变量、访问其成员，以及如何通过值和指针将结构体传递给函数。最后，我们还会了解如何使用`typedef`关键字为结构体创建别名，以简化代码。

## 定义结构体

![](img/c027cd881a09cfe95dd09079c3f66e22_1.png)

![](img/c027cd881a09cfe95dd09079c3f66e22_3.png)

结构体在C语言中用于创建自定义的复合数据类型。与Java或C++中的类不同，C的结构体只包含数据成员，不包含函数。

![](img/c027cd881a09cfe95dd09079c3f66e22_5.png)

![](img/c027cd881a09cfe95dd09079c3f66e22_7.png)

定义一个结构体的基本语法如下：
```c
struct 结构体名 {
    数据类型 成员1;
    数据类型 成员2;
    // ... 更多成员
};
```

![](img/c027cd881a09cfe95dd09079c3f66e22_9.png)

![](img/c027cd881a09cfe95dd09079c3f66e22_11.png)

![](img/c027cd881a09cfe95dd09079c3f66e22_13.png)

例如，我们可以定义一个表示学生的结构体：
```c
struct student {
    char *name; // 姓名，字符指针
    int id;     // 学号，整数
};
```
这里，`struct student`是一个新的数据类型，它包含两个成员：一个指向字符串的指针`name`和一个整数`id`。

![](img/c027cd881a09cfe95dd09079c3f66e22_15.png)

## 创建和使用结构体变量

定义了结构体类型后，我们就可以声明该类型的变量，并为其成员赋值。

![](img/c027cd881a09cfe95dd09079c3f66e22_17.png)

![](img/c027cd881a09cfe95dd09079c3f66e22_19.png)

以下是创建结构体变量并访问其成员的步骤：
1.  **声明变量**：使用结构体类型声明一个变量。
2.  **访问成员**：使用点运算符（`.`）来访问结构体变量的成员。

![](img/c027cd881a09cfe95dd09079c3f66e22_21.png)

![](img/c027cd881a09cfe95dd09079c3f66e22_23.png)

![](img/c027cd881a09cfe95dd09079c3f66e22_25.png)

示例代码如下：
```c
#include <stdio.h>

![](img/c027cd881a09cfe95dd09079c3f66e22_27.png)

struct student {
    char *name;
    int id;
};

int main() {
    // 声明一个student类型的变量
    struct student student1;

    // 为结构体成员赋值
    student1.name = "Mike";
    student1.id = 123456;

    // 打印结构体成员
    printf("Name: %s\n", student1.name);
    printf("ID: %d\n", student1.id);

    return 0;
}
```
编译并运行这段代码，将输出学生的姓名和学号。

## 结构体在内存中的布局

![](img/c027cd881a09cfe95dd09079c3f66e22_29.png)

![](img/c027cd881a09cfe95dd09079c3f66e22_30.png)

为了理解结构体在内存中是如何存储的，我们可以打印出结构体及其成员的地址。

![](img/c027cd881a09cfe95dd09079c3f66e22_32.png)

![](img/c027cd881a09cfe95dd09079c3f66e22_34.png)

以下是查看地址的代码示例：
```c
printf("Address of student struct: %p\n", &student1);
printf("Address of student.name: %p\n", &(student1.name));
printf("Address of student.id: %p\n", &(student1.id));
```
运行后，你会发现结构体变量的地址与其第一个成员（`name`）的地址相同。这表明结构体在内存中是连续存储的，起始地址就是第一个成员的地址。

![](img/c027cd881a09cfe95dd09079c3f66e22_36.png)

![](img/c027cd881a09cfe95dd09079c3f66e22_38.png)

字符串字面量（如`"Mike"`）通常存储在内存的只读区域（文本段），其地址远大于栈上局部变量（如`student1`）的地址。结构体中的`name`指针存储的正是这个字符串的地址。

![](img/c027cd881a09cfe95dd09079c3f66e22_40.png)

## 将结构体传递给函数

![](img/c027cd881a09cfe95dd09079c3f66e22_42.png)

在C语言中，函数参数默认是“按值传递”。这意味着当我们将一个结构体传递给函数时，函数内部会得到该结构体的一个完整副本。

### 按值传递结构体

以下是一个按值传递结构体的函数示例：
```c
void printStudent(struct student s) {
    printf("Name (in function): %s\n", s.name);
    printf("ID (in function): %d\n", s.id);
    printf("Address of s in function: %p\n", &s);
}

![](img/c027cd881a09cfe95dd09079c3f66e22_44.png)

int main() {
    struct student student1 = {"Mike", 123456};
    printStudent(student1); // 传递结构体副本
    return 0;
}
```
在函数`printStudent`内部，参数`s`是`student1`的一个完整拷贝，它拥有自己独立的内存空间。修改`s`的成员不会影响`main`函数中的`student1`。

![](img/c027cd881a09cfe95dd09079c3f66e22_46.png)

![](img/c027cd881a09cfe95dd09079c3f66e22_47.png)

![](img/c027cd881a09cfe95dd09079c3f66e22_48.png)

![](img/c027cd881a09cfe95dd09079c3f66e22_50.png)

![](img/c027cd881a09cfe95dd09079c3f66e22_52.png)

![](img/c027cd881a09cfe95dd09079c3f66e22_54.png)

对于大型结构体，这种复制方式会消耗较多时间和内存。

![](img/c027cd881a09cfe95dd09079c3f66e22_56.png)

### 按指针传递结构体

![](img/c027cd881a09cfe95dd09079c3f66e22_58.png)

![](img/c027cd881a09cfe95dd09079c3f66e22_59.png)

![](img/c027cd881a09cfe95dd09079c3f66e22_61.png)

更高效的方式是传递指向结构体的指针。这样，函数内部操作的是原始数据，避免了复制整个结构体的开销。

![](img/c027cd881a09cfe95dd09079c3f66e22_63.png)

![](img/c027cd881a09cfe95dd09079c3f66e22_65.png)

当使用指针时，我们需要使用箭头运算符（`->`）来访问结构体成员。

以下是一个按指针传递结构体的函数示例：
```c
void printStudentByPointer(struct student *s) {
    // 使用箭头运算符访问成员
    printf("Name (via pointer): %s\n", s->name);
    printf("ID (via pointer): %d\n", s->id);
    printf("Address of pointer s: %p\n", s); // s本身存储的是地址
}

![](img/c027cd881a09cfe95dd09079c3f66e22_67.png)

int main() {
    struct student student1 = {"Mike", 123456};
    printStudentByPointer(&student1); // 传递结构体的地址
    return 0;
}
```
在`printStudentByPointer`函数中，参数`s`是一个指向`struct student`的指针。我们通过`&student1`将`student1`的地址传递给函数。函数内部通过`s->name`和`s->id`来访问原始结构体的成员。

箭头运算符`->`是解引用和成员访问的组合简写，`s->name`等价于`(*s).name`。

## 使用typedef简化结构体

![](img/c027cd881a09cfe95dd09079c3f66e22_69.png)

![](img/c027cd881a09cfe95dd09079c3f66e22_71.png)

在C代码中反复书写`struct student`可能会显得冗长。我们可以使用`typedef`关键字为结构体类型创建一个别名。

使用`typedef`有两种常见方式：

![](img/c027cd881a09cfe95dd09079c3f66e22_73.png)

![](img/c027cd881a09cfe95dd09079c3f66e22_74.png)

![](img/c027cd881a09cfe95dd09079c3f66e22_76.png)

![](img/c027cd881a09cfe95dd09079c3f66e22_78.png)

**方式一：先定义结构体，再创建别名**
```c
struct student {
    char *name;
    int id;
};
typedef struct student Student; // 现在可以用Student代替struct student

![](img/c027cd881a09cfe95dd09079c3f66e22_80.png)

![](img/c027cd881a09cfe95dd09079c3f66e22_81.png)

Student stu1; // 声明变量
```

![](img/c027cd881a09cfe95dd09079c3f66e22_83.png)

![](img/c027cd881a09cfe95dd09079c3f66e22_85.png)

**方式二：在定义结构体的同时创建别名（更简洁）**
```c
typedef struct {
    char *name;
    int id;
} Student; // Student 就是新类型的名字

Student stu1; // 声明变量
```
使用别名后，代码变得更加简洁。`typedef`的另一个常见用途是为基本类型创建别名，以便于未来统一修改类型，例如将程序中所有`float`改为`double`只需修改一处`typedef`定义。

![](img/c027cd881a09cfe95dd09079c3f66e22_87.png)

![](img/c027cd881a09cfe95dd09079c3f66e22_89.png)

![](img/c027cd881a09cfe95dd09079c3f66e22_91.png)

本节课中我们一起学习了C语言结构体的核心知识。我们了解了如何定义和初始化结构体，如何访问其成员，以及结构体在内存中的布局。我们还探讨了通过值和指针两种方式将结构体传递给函数的区别与优劣，并学会了使用`typedef`来简化结构体类型名。掌握结构体是组织复杂数据的基础，对于后续学习数据结构和系统编程至关重要。