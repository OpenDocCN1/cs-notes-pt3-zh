# 计算机编程：从Bash到Rust：07：Rust字符串、切片与结构体 🦀

在本节课中，我们将学习Rust中的两个核心概念：**切片**和**结构体**。切片允许我们引用集合中的一部分连续元素，而结构体则是一种自定义数据类型，用于将多个相关的值组合成一个有意义的组。课程最后，我们将通过一个综合性的知识问答来复习至今为止学到的所有内容。

## 切片类型与字符串切片 🔪

上一节我们回顾了所有权和内存访问。本节中，我们来看看**切片**。切片允许我们引用一个集合中一段连续的元素序列，而不是引用整个集合。

![](img/88cd40dc273c9b3c120243d4187bdf7c_1.png)

### 什么是切片？

![](img/88cd40dc273c9b3c120243d4187bdf7c_3.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_5.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_7.png)

切片是对集合中一部分数据的引用，它本身不拥有数据的所有权。这在处理长字符串时非常有用，例如，我们想获取字符串中的第一个单词。

字符串切片看起来像普通的引用，但在末尾有一个方括号，里面包含两个用`..`分隔的数字，表示起始和结束索引（结束索引不包含在内）。

**公式**：`&variable_name[start_index..end_index]`

例如，对于一个字符串`let s = “reverse me”;`，切片`&s[0..7]`将得到`”reverse”`。

### 切片的工作原理

在内存中，一个字符串切片内部存储了一个指向起始位置的指针和切片的长度（`结束索引 - 起始索引`）。

以下是字符串切片的一个代码示例：
```rust
let reverse_me = String::from("reverse me");
let word_one = &reverse_me[0..7]; // 获取 “reverse”
let word_two = &reverse_me[8..10]; // 获取 “me”
println!("{} {}", word_two, word_one); // 输出 “me reverse”
```

### 切片的便捷语法

Rust提供了一些便捷的切片语法：
*   `&s[..5]`：从开头到索引5（不包含）。
*   `&s[3..]`：从索引3到字符串结尾。
*   `&s[..]`：获取整个字符串的切片。

字符串字面量（如`let s = “hello”;`）本身就是字符串切片（`&str`类型），这也是它们不可变的原因。

### 其他类型的切片

切片不仅限于字符串，也可以用于数组等其他集合。
```rust
let arr = [1, 3, 9, 6, 7];
let slice = &arr[1..3]; // 引用 [9, 6]
```

## 结构体 🏗️

![](img/88cd40dc273c9b3c120243d4187bdf7c_9.png)

现在，让我们转向**结构体**。结构体是一种自定义数据类型，它允许你将多个相关的值组合成一个有意义的组，这与仅仅存储同类型元素的集合（如数组）不同。

![](img/88cd40dc273c9b3c120243d4187bdf7c_11.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_13.png)

### 定义与实例化结构体

![](img/88cd40dc273c9b3c120243d4187bdf7c_15.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_16.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_18.png)

要定义一个结构体，使用`struct`关键字，后跟结构体名称和花括号。在花括号内，定义字段名及其类型。

![](img/88cd40dc273c9b3c120243d4187bdf7c_20.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_22.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_24.png)

**代码**：
```rust
struct UIUCStudent {
    name: String,
    uin: u32,
    is_cs196: bool,
    gpa: f32,
}
```

要创建结构体的一个实例（即声明一个结构体变量），使用`let`关键字，并按任意顺序为字段赋值。

**代码**：
```rust
let student1 = UIUCStudent {
    name: String::from("CS 196"),
    uin: 123456789,
    is_cs196: true,
    gpa: 4.0,
};
```

### 访问与修改结构体字段

![](img/88cd40dc273c9b3c120243d4187bdf7c_26.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_28.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_30.png)

使用点号（`.`）后跟字段名来访问结构体实例中的值。

![](img/88cd40dc273c9b3c120243d4187bdf7c_32.png)

**代码**：
```rust
println!("Student name: {}", student1.name);
```

![](img/88cd40dc273c9b3c120243d4187bdf7c_34.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_36.png)

要修改结构体字段的值，整个结构体实例必须是可变的。Rust不允许结构体的部分字段可变，必须是整个实例要么全部可变，要么全部不可变。

![](img/88cd40dc273c9b3c120243d4187bdf7c_38.png)

**代码**：
```rust
let mut student_mut = student1;
student_mut.gpa = 3.3; // 允许修改
```

### 使用函数创建结构体

![](img/88cd40dc273c9b3c120243d4187bdf7c_40.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_41.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_43.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_44.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_46.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_47.png)

我们可以编写一个函数来创建并返回结构体实例。在函数内部，我们可以预设一些字段的值。

![](img/88cd40dc273c9b3c120243d4187bdf7c_49.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_51.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_53.png)

**代码**：
```rust
fn new_student(name: String, uin: u32) -> UIUCStudent {
    UIUCStudent {
        name,
        uin,
        is_cs196: true, // 预设值
        gpa: 4.0,       // 预设值
    }
}
```
注意，当函数参数名与结构体字段名相同时，可以使用**字段初始化简写语法**，无需重复书写`name: name`。

![](img/88cd40dc273c9b3c120243d4187bdf7c_55.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_57.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_58.png)

### 结构体更新语法

![](img/88cd40dc273c9b3c120243d4187bdf7c_60.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_62.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_63.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_65.png)

当你想基于一个已有的结构体实例创建新实例，并只更新部分字段时，可以使用结构体更新语法`..`，这能避免大量重复代码。

![](img/88cd40dc273c9b3c120243d4187bdf7c_67.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_68.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_70.png)

**代码**：
```rust
let student2 = UIUCStudent {
    name: String::from("Another Student"),
    uin: 987654321,
    ..student1 // 其余字段使用 student1 的值
};
```

![](img/88cd40dc273c9b3c120243d4187bdf7c_71.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_73.png)

### 元组结构体

![](img/88cd40dc273c9b3c120243d4187bdf7c_75.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_76.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_78.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_80.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_81.png)

元组结构体类似于元组，但拥有一个具体的类型名。它的字段没有名称，只有类型。当你需要多次使用一种特定类型的元组时，这很有用。

![](img/88cd40dc273c9b3c120243d4187bdf7c_82.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_84.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_86.png)

**代码**：
```rust
struct TestScores(i32, i32, i32);
struct LectureReviews(i32, i32, i32);

![](img/88cd40dc273c9b3c120243d4187bdf7c_88.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_89.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_91.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_93.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_94.png)

let midterm = TestScores(85, 90, 78);
// midterm.0, midterm.1, midterm.2 访问值
```
即使`TestScores`和`LectureReviews`包含相同类型的字段，它们也是不同的类型，不能互换使用。

![](img/88cd40dc273c9b3c120243d4187bdf7c_96.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_97.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_99.png)

## 知识问答复习 📝

![](img/88cd40dc273c9b3c120243d4187bdf7c_101.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_103.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_104.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_106.png)

以下是本节课涵盖及之前课程的部分核心概念问答，用于巩固理解：

![](img/88cd40dc273c9b3c120243d4187bdf7c_108.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_110.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_111.png)

1.  **变量默认状态**：Rust中的变量默认是**不可变**的。
2.  **使变量可变**：使用`mut`关键字可以使变量可变，例如`let mut x = 5;`。
3.  **标量类型**：标量类型代表单个值，如整数、浮点数、布尔值和字符。
4.  **复合类型**：复合类型可以包含多个值，如数组和元组。
5.  **数组元素类型**：数组中的所有元素必须是**相同**类型。
6.  **栈与堆**：栈用于存储大小固定的数据，堆用于存储大小未知或可能变化的数据。
7.  **编程目标**：程序员通常追求更高的性能。
8.  **所有权规则**：在Rust中，一个值在任意时刻只能有**一个**所有者。
9.  **编程范式**：Rust是一种**多范式**编程语言。
10. **定义与声明**：使用`struct`关键字**定义**结构体类型，使用`let`关键字**声明**结构体实例。
11. **函数与所有权**：函数通常会获取传入参数的**所有权**，除非特别说明（如使用引用）。
12. **切片的本质**：切片是**引用**，不拥有数据。
13. **访问结构体字段**：使用**点表示法**（`.`）访问结构体字段。
14. **结构体可变性**：结构体的可变性是针对**整个实例**的，不能单独指定某个字段可变。
15. **字符串切片内容**：字符串切片内部存储**指针**和**长度**，但不存储容量。

![](img/88cd40dc273c9b3c120243d4187bdf7c_113.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_114.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_116.png)

## 总结 🎯

![](img/88cd40dc273c9b3c120243d4187bdf7c_118.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_120.png)

本节课中我们一起学习了Rust的两个重要特性：切片和结构体。切片提供了一种高效引用部分数据的方式，而结构体则帮助我们创建有组织的自定义数据类型。通过理解这些概念并进行实践，你将能更好地组织和管理Rust程序中的数据。下节课我们将暂时离开新的Rust概念，学习如何进行调试和编写更健壮的代码。