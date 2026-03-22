# 002：Rust基础与所有权

![](img/042151d916811275d23bad7ab98e62e8_1.png)

## 概述

![](img/042151d916811275d23bad7ab98e62e8_3.png)

在本节课中，我们将要学习Rust编程语言的基础知识，包括变量与可变性、数据类型、表达式、函数、控制流，并初步接触Rust的核心概念——所有权。

---

![](img/042151d916811275d23bad7ab98e62e8_5.png)

![](img/042151d916811275d23bad7ab98e62e8_7.png)

## 变量与可变性

在Rust中，我们使用 `let` 关键字来声明变量。默认情况下，所有绑定都是不可变的。

```rust
let x = 42; // 不可变绑定
```

如果你希望一个变量可以被修改，必须显式地使用 `mut` 关键字。

```rust
let mut x = 42;
x = x * 2; // 这是允许的
```

### 变量遮蔽

Rust允许你重新声明一个同名变量，这被称为“遮蔽”。新变量会“遮蔽”掉旧的同名变量，它们可以是完全不同的类型。

![](img/042151d916811275d23bad7ab98e62e8_9.png)

![](img/042151d916811275d23bad7ab98e62e8_11.png)

```rust
let x = 42; // x 是 i32
let x = 'c'; // x 现在是 char，遮蔽了之前的 x
```

### 常量

![](img/042151d916811275d23bad7ab98e62e8_13.png)

![](img/042151d916811275d23bad7ab98e62e8_15.png)

![](img/042151d916811275d23bad7ab98e62e8_17.png)

你可以使用 `const` 关键字定义常量。常量必须显式指定类型，并且其值在编译时必须是已知的。

```rust
const F: i32 = 42;
```

---

## 数据类型

![](img/042151d916811275d23bad7ab98e62e8_19.png)

![](img/042151d916811275d23bad7ab98e62e8_20.png)

Rust是一种静态类型语言，这意味着所有变量的类型在编译时都是已知的。编译器通常可以推断出类型，但有时也需要你显式标注。

### 标量类型

标量类型代表单个值。Rust有四种主要的标量类型：整数、浮点数、布尔值和字符。

*   **整数**：有符号（`i8`, `i16`, `i32`, `i64`, `i128`）和无符号（`u8`, `u16`, `u32`, `u64`, `u128`）。`i32` 和 `u32` 是常用类型。
*   **浮点数**：`f32`（单精度）和 `f64`（双精度）。
*   **布尔值**：`bool`，值为 `true` 或 `false`。
*   **字符**：`char`，表示一个Unicode标量值。

![](img/042151d916811275d23bad7ab98e62e8_22.png)

![](img/042151d916811275d23bad7ab98e62e8_24.png)

### 复合类型

复合类型可以将多个值组合成一个类型。Rust有两个原生的复合类型：元组和数组。

*   **元组**：将多个不同类型的值组合在一起。长度固定。

    ```rust
    let tup: (i32, bool, char) = (42, true, 'z');
    // 通过模式匹配解构
    let (x, y, z) = tup;
    // 通过索引访问
    let first = tup.0;
    ```

*   **数组**：将多个相同类型的值组合在一起。长度固定。

    ```rust
    let arr: [i32; 3] = [1, 2, 3];
    let first = arr[0]; // 索引从0开始
    ```

### 结构体与枚举

上一节我们介绍了基础的数据容器，本节中我们来看看如何定义自己的复合类型。

![](img/042151d916811275d23bad7ab98e62e8_26.png)

*   **结构体**：为数据命名并打包，使其意义更清晰。

    ```rust
    struct Student {
        zid: String,
        age: u32,
        wam: Option<f64>,
    }
    let student = Student { zid: String::from("z1234567"), age: 20, wam: Some(85.5) };
    ```

![](img/042151d916811275d23bad7ab98e62e8_28.png)

*   **枚举**：定义一个类型可能取值的集合。Rust的枚举非常强大，每个变体可以关联不同类型和数量的数据。

    ```rust
    enum Automobile {
        Car { make: String, model: String, doors: u8, driven_wheels: DriveType },
        Motorbike { make: String, model: String, horsepower: u32 },
        Train { capacity: u32 },
        Bus { capacity: u32 },
    }
    ```

### 单元类型

单元类型 `()` 是一个零长度的元组。它通常在不关心返回值，但又需要某种类型时使用，例如不返回任何有用值的函数。

```rust
let unit: () = ();
```

---

## Rust作为表达式语言

![](img/042151d916811275d23bad7ab98e62e8_30.png)

![](img/042151d916811275d23bad7ab98e62e8_31.png)

在Rust中，几乎所有代码块都是表达式，这意味着它们会产生一个值。这与许多语言中的“语句”概念不同。

![](img/042151d916811275d23bad7ab98e62e8_33.png)

![](img/042151d916811275d23bad7ab98e62e8_35.png)

![](img/042151d916811275d23bad7ab98e62e8_37.png)

例如，`if` 在Rust中是一个表达式：

```rust
let x = if condition { 42 } else { 100 }; // x 会根据条件被赋值为 42 或 100
```

![](img/042151d916811275d23bad7ab98e62e8_39.png)

![](img/042151d916811275d23bad7ab98e62e8_41.png)

函数体中的最后一个表达式（没有分号）会自动成为该函数的返回值：

```rust
fn add(a: i32, b: i32) -> i32 {
    a + b // 没有分号，这是一个表达式，其值 `a+b` 被返回
}
```

---

## 函数

函数使用 `fn` 关键字定义。参数和返回值的类型必须显式声明。

```rust
fn greet(name: &str) -> String {
    format!("Hello, {}!", name)
}
```

---

![](img/042151d916811275d23bad7ab98e62e8_43.png)

![](img/042151d916811275d23bad7ab98e62e8_45.png)

## 控制流

![](img/042151d916811275d23bad7ab98e62e8_47.png)

![](img/042151d916811275d23bad7ab98e62e8_48.png)

![](img/042151d916811275d23bad7ab98e62e8_49.png)

![](img/042151d916811275d23bad7ab98e62e8_50.png)

![](img/042151d916811275d23bad7ab98e62e8_52.png)

Rust提供了常见的控制流结构：`if`、`loop`、`while`、`for` 和强大的 `match`。

![](img/042151d916811275d23bad7ab98e62e8_54.png)

![](img/042151d916811275d23bad7ab98e62e8_55.png)

![](img/042151d916811275d23bad7ab98e62e8_56.png)

### 条件与循环

*   `if` 表达式：条件必须是 `bool` 类型。
*   `loop`：无限循环，可以使用 `break` 退出，`break` 可以带一个返回值。
*   `while`：条件循环。
*   `for`：遍历集合（如数组、范围等）。

### 模式匹配

![](img/042151d916811275d23bad7ab98e62e8_58.png)

![](img/042151d916811275d23bad7ab98e62e8_60.png)

![](img/042151d916811275d23bad7ab98e62e8_61.png)

![](img/042151d916811275d23bad7ab98e62e8_63.png)

![](img/042151d916811275d23bad7ab98e62e8_65.png)

![](img/042151d916811275d23bad7ab98e62e8_67.png)

`match` 表达式允许你将一个值与一系列模式进行比较，并根据匹配的模式执行代码。它是**穷尽**的，意味着必须覆盖所有可能的情况。

```rust
match value {
    1 => println!("One"),
    2 | 3 | 4 | 5 => println!("Two through Five"),
    _ => println!("Something else"), // `_` 通配符匹配任何值
}
```

![](img/042151d916811275d23bad7ab98e62e8_69.png)

![](img/042151d916811275d23bad7ab98e62e8_70.png)

![](img/042151d916811275d23bad7ab98e62e8_72.png)

![](img/042151d916811275d23bad7ab98e62e8_73.png)

![](img/042151d916811275d23bad7ab98e62e8_75.png)

![](img/042151d916811275d23bad7ab98e62e8_76.png)

`match` 在处理枚举和 `Option`/`Result` 类型时尤其有用：

```rust
let some_number: Option<i32> = Some(5);
match some_number {
    Some(x) => println!("The number is: {}", x),
    None => println!("There is no number"),
}
```

---

## 所有权

所有权是Rust最独特的功能，它使Rust能够在没有垃圾回收的情况下保证内存安全。

![](img/042151d916811275d23bad7ab98e62e8_78.png)

![](img/042151d916811275d23bad7ab98e62e8_80.png)

![](img/042151d916811275d23bad7ab98e62e8_82.png)

### 核心规则

1.  Rust中的每个值都有一个被称为其**所有者**的变量。
2.  值在任一时刻有且只有一个所有者。
3.  当所有者（变量）离开作用域，这个值将被丢弃（`drop`）。

### 移动语义

对于非 `Copy` 类型（如 `String`, `Vec`），赋值或传参会导致**所有权移动**。移动后，原来的变量将失效，不能再被使用。

```rust
let s1 = String::from("hello");
let s2 = s1; // s1 的所有权移动到了 s2
// println!("{}", s1); // 错误！s1 不再有效
```

### 克隆

![](img/042151d916811275d23bad7ab98e62e8_84.png)

![](img/042151d916811275d23bad7ab98e62e8_85.png)

如果你确实需要深度复制堆上的数据，可以使用 `clone` 方法。这会产生数据的完整副本，两个变量彼此独立。

```rust
let s1 = String::from("hello");
let s2 = s1.clone(); // 显式克隆
println!("{} and {}", s1, s2); // 现在两者都有效
```

![](img/042151d916811275d23bad7ab98e62e8_87.png)

![](img/042151d916811275d23bad7ab98e62e8_89.png)

### Copy 类型

![](img/042151d916811275d23bad7ab98e62e8_91.png)

对于存储在栈上的简单标量类型（如整数、布尔值、字符）以及完全由 `Copy` 类型组成的元组和结构体，赋值会进行**拷贝**，而不是移动。`Copy` 类型自动实现了 `Copy` trait。

![](img/042151d916811275d23bad7ab98e62e8_93.png)

![](img/042151d916811275d23bad7ab98e62e8_95.png)

```rust
let x = 5;
let y = x; // x 被拷贝到 y
println!("x = {}, y = {}", x, y); // 两者都有效
```

![](img/042151d916811275d23bad7ab98e62e8_97.png)

### 所有权与函数

将值传递给函数时，所有权可能会发生移动。函数返回值也可以转移所有权。

![](img/042151d916811275d23bad7ab98e62e8_99.png)

![](img/042151d916811275d23bad7ab98e62e8_101.png)

![](img/042151d916811275d23bad7ab98e62e8_103.png)

```rust
fn takes_ownership(s: String) -> String { // s 进入作用域
    println!("{}", s);
    s // s 作为返回值被移出
}

fn main() {
    let s1 = String::from("hello");
    let s2 = takes_ownership(s1); // s1 的所有权被移动到函数内，然后又被移动到 s2
    // s1 在这里不再有效
}
```

---

## 总结

![](img/042151d916811275d23bad7ab98e62e8_105.png)

![](img/042151d916811275d23bad7ab98e62e8_107.png)

本节课中我们一起学习了Rust的基础语法和核心概念。我们了解了变量声明、可变性、各种数据类型（标量、复合、结构体、枚举），体验了Rust强大的表达式特性，学习了函数定义和控制流（特别是模式匹配）。最后，我们初步接触了Rust独特的所有权系统，理解了移动、克隆和 `Copy` 类型的区别，这是写出安全、高效Rust代码的基石。在接下来的课程中，我们将深入探讨借用、生命周期等更高级的所有权相关主题。