# 005：Rust入门 - 变量、类型、函数与控制流 🦀

![](img/6e5d51dd66a2cde6b882038389bd2645_1.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_3.png)

在本节课中，我们将学习Rust编程语言的基础知识。Rust是一门注重安全与性能的系统编程语言。我们将从如何编写第一个Rust程序开始，逐步了解变量、数据类型、函数以及控制流等核心概念。

## Rust简介与安装 🛠️

Rust是一门多范式系统编程语言。这意味着它不局限于单一的编程风格，并且专注于构建高性能、安全的系统软件。与C++等语言相比，Rust在保持高性能的同时，通过编译器提供了更强的内存安全和类型安全保障。

要开始使用Rust，首先需要安装它。你可以通过访问Rust官方文档获取安装指南。安装完成后，你可以通过终端命令 `rustc --version` 来验证安装是否成功。

Rust源文件以 `.rs` 扩展名结尾。要编译一个Rust文件，可以使用 `rustc` 命令，例如 `rustc main.rs`。这将生成一个可执行文件。

## 第一个Rust程序：Hello World 🌍

所有Rust程序的执行都始于 `main` 函数。这是一个特殊的函数，编译器会首先运行它。

下面是一个简单的“Hello World”程序：

```rust
fn main() {
    println!("Hello, world!");
}
```

![](img/6e5d51dd66a2cde6b882038389bd2645_5.png)

在这段代码中：
*   `fn` 关键字用于声明一个函数。
*   `main` 是函数名。
*   `println!` 是一个Rust宏（由 `!` 标识），用于向终端输出一行文本。
*   每一行代码的结尾需要加上分号 `;`。

![](img/6e5d51dd66a2cde6b882038389bd2645_7.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_9.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_11.png)

将上述代码保存为 `hello.rs`，然后在终端中运行 `rustc hello.rs` 进行编译，再运行生成的可执行文件 `./hello`，你将在屏幕上看到“Hello, world!”。

![](img/6e5d51dd66a2cde6b882038389bd2645_13.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_15.png)

## 使用Cargo管理项目 📦

![](img/6e5d51dd66a2cde6b882038389bd2645_17.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_19.png)

对于更复杂的项目，推荐使用Cargo，它是Rust内置的构建系统和包管理器。Cargo可以自动处理代码构建、依赖下载和项目管理。

![](img/6e5d51dd66a2cde6b882038389bd2645_21.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_23.png)

你可以使用 `cargo --version` 检查Cargo是否已安装。

![](img/6e5d51dd66a2cde6b882038389bd2645_25.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_27.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_29.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_31.png)

要创建一个新的Cargo项目，请使用 `cargo new project_name` 命令。这会创建一个包含以下结构的目录：
*   `src/` 目录：存放源代码，其中包含一个初始的 `main.rs` 文件。
*   `Cargo.toml` 文件：项目的配置文件，用于管理元信息和依赖。
*   `.git` 目录：初始化的Git仓库。

![](img/6e5d51dd66a2cde6b882038389bd2645_33.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_35.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_37.png)

在项目目录中，你可以使用以下常用命令：
*   `cargo build`：编译项目，在 `target/debug/` 目录下生成可调试的可执行文件。
*   `cargo run`：编译并立即运行项目。
*   `cargo check`：快速检查代码是否能通过编译，而不生成可执行文件，速度更快。
*   `cargo build --release`：以发布模式编译，在 `target/release/` 目录下生成经过高度优化的可执行文件，但编译时间更长。

![](img/6e5d51dd66a2cde6b882038389bd2645_39.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_41.png)

## 变量与可变性 📊

在Rust中，变量默认是**不可变的**。这意味着一旦给变量赋值，就不能再更改它的值。这有助于提高代码的安全性和清晰度，尤其是在并发编程中。

![](img/6e5d51dd66a2cde6b882038389bd2645_43.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_45.png)

声明变量使用 `let` 关键字：
```rust
let x = 5; // x是不可变的
```
尝试修改 `x` 的值会导致编译错误。

![](img/6e5d51dd66a2cde6b882038389bd2645_47.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_49.png)

如果你需要一个可以改变的变量，需要使用 `mut` 关键字将其声明为**可变的**：
```rust
let mut y = 5;
y = 10; // 这是允许的
println!("y 的值是: {}", y);
```

![](img/6e5d51dd66a2cde6b882038389bd2645_51.png)

Rust还支持**变量遮蔽**。这意味着你可以使用 `let` 关键字再次声明一个同名变量，新的变量会“遮蔽”旧的变量，并且可以拥有不同的类型：
```rust
let spaces = "   ";
let spaces = spaces.len(); // 遮蔽：将字符串转换为它的长度（整数）
```
这与使用 `mut` 修改变量是不同的概念。

![](img/6e5d51dd66a2cde6b882038389bd2645_53.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_55.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_57.png)

## 数据类型 🧮

Rust是静态类型语言，这意味着编译器必须在编译时知道所有变量的类型。编译器通常可以根据值推断出类型，但有时也需要显式标注。

![](img/6e5d51dd66a2cde6b882038389bd2645_59.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_61.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_63.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_65.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_66.png)

Rust的数据类型主要分为两类：标量类型和复合类型。

![](img/6e5d51dd66a2cde6b882038389bd2645_68.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_70.png)

### 标量类型

标量类型代表单个值。Rust有四种基本的标量类型：

1.  **整数**：没有小数部分的数字。分为有符号（`i8`, `i16`, `i32`, `i64`, `isize`）和无符号（`u8`, `u16`, `u32`, `u64`, `usize`）。`i32` 和 `u32` 是默认类型。
    ```rust
    let a: i32 = -10;
    let b: u64 = 100;
    ```

![](img/6e5d51dd66a2cde6b882038389bd2645_72.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_74.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_75.png)

2.  **浮点数**：带有小数点的数字。有 `f32` 和 `f64` 两种，`f64` 是默认类型，精度更高。
    ```rust
    let c = 3.14; // f64
    let d: f32 = 2.5; // f32
    ```

![](img/6e5d51dd66a2cde6b882038389bd2645_77.png)

3.  **布尔值**：只能是 `true` 或 `false`。
    ```rust
    let is_rust_cool: bool = true;
    ```

![](img/6e5d51dd66a2cde6b882038389bd2645_79.png)

4.  **字符**：使用单引号声明，代表一个Unicode标量值，可以存储字母、数字、汉字甚至表情符号。
    ```rust
    let emoji = '😀';
    let chinese_char = '中';
    ```

![](img/6e5d51dd66a2cde6b882038389bd2645_81.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_83.png)

### 复合类型

![](img/6e5d51dd66a2cde6b882038389bd2645_85.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_87.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_89.png)

复合类型可以将多个值组合成一个类型。Rust有两个原生的复合类型：元组和数组。

![](img/6e5d51dd66a2cde6b882038389bd2645_91.png)

1.  **元组**：可以将多个不同类型的值组合在一起。元组有固定的长度。
    ```rust
    let tup: (i32, f64, char) = (500, 6.4, 'J');
    // 通过解构访问
    let (x, y, z) = tup;
    println!("y 的值是: {}", y); // 输出 6.4
    // 通过索引访问（从0开始）
    println!("第一个元素是: {}", tup.0); // 输出 500
    ```

![](img/6e5d51dd66a2cde6b882038389bd2645_93.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_95.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_97.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_99.png)

2.  **数组**：每个元素必须是相同类型，并且有固定的长度。
    ```rust
    let arr = [1, 2, 3, 4, 5];
    let first = arr[0]; // 访问第一个元素
    let second = arr[1]; // 访问第二个元素
    // 声明一个包含5个相同元素的数组
    let same_arr = [3; 5]; // 等同于 [3, 3, 3, 3, 3]
    ```
    访问数组元素时，如果索引超出范围，程序会在**运行时**崩溃（panic），这是Rust安全机制的一部分。

![](img/6e5d51dd66a2cde6b882038389bd2645_101.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_103.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_105.png)

## 控制流 🔀

![](img/6e5d51dd66a2cde6b882038389bd2645_107.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_108.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_109.png)

控制流允许你根据条件决定执行哪部分代码，或者重复执行某段代码。

![](img/6e5d51dd66a2cde6b882038389bd2645_111.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_113.png)

### 条件分支：`if` 表达式

![](img/6e5d51dd66a2cde6b882038389bd2645_115.png)

`if` 表达式允许你根据条件执行不同的代码分支。在Rust中，`if` 是一个表达式，意味着它可以返回一个值。
```rust
let number = 6;

![](img/6e5d51dd66a2cde6b882038389bd2645_117.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_119.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_121.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_122.png)

if number % 2 == 0 {
    println!("数字是偶数");
} else {
    println!("数字是奇数");
}

![](img/6e5d51dd66a2cde6b882038389bd2645_124.png)

// if 表达式返回值
let result = if number > 5 { "大" } else { "小" };
println!("数字是{}的", result);
```
注意，每个条件分支返回的值必须是相同类型。

![](img/6e5d51dd66a2cde6b882038389bd2645_126.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_128.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_130.png)

### 循环

![](img/6e5d51dd66a2cde6b882038389bd2645_132.png)

Rust提供了几种循环方式：`loop`、`while` 和 `for`。

![](img/6e5d51dd66a2cde6b882038389bd2645_134.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_136.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_138.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_140.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_142.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_143.png)

1.  **`loop`**：无限循环，直到遇到 `break` 关键字。`loop` 也可以返回值。
    ```rust
    let mut counter = 0;
    let result = loop {
        counter += 1;
        if counter == 10 {
            break counter * 2; // 跳出循环并返回值
        }
    };
    println!("结果是: {}", result); // 输出 20
    ```

![](img/6e5d51dd66a2cde6b882038389bd2645_145.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_147.png)

2.  **`while`**：在条件为 `true` 时循环。
    ```rust
    let mut number = 3;
    while number != 0 {
        println!("{}!", number);
        number -= 1;
    }
    println!("发射!");
    ```

![](img/6e5d51dd66a2cde6b882038389bd2645_149.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_150.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_152.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_154.png)

3.  **`for`**：最常用、最安全的循环，用于遍历集合。
    ```rust
    let arr = [10, 20, 30, 40, 50];
    for element in arr.iter() {
        println!("值是: {}", element);
    }
    // 使用范围
    for number in 1..4 { // 不包含4
        println!("{}!", number);
    }
    ```

![](img/6e5d51dd66a2cde6b882038389bd2645_156.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_158.png)

## 注释 💬

![](img/6e5d51dd66a2cde6b882038389bd2645_160.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_162.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_164.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_166.png)

注释用于解释代码，编译器会忽略它们。Rust使用 `//` 来开始一行注释。
```rust
// 这是一个单行注释
let lucky_number = 7; // 这也是一个注释

![](img/6e5d51dd66a2cde6b882038389bd2645_168.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_169.png)

/*
这是一个
多行注释块
*/
```
在大多数代码编辑器中，你可以使用快捷键（如 `Ctrl + /` 或 `Cmd + /`）快速注释或取消注释选中的代码行。

![](img/6e5d51dd66a2cde6b882038389bd2645_171.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_172.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_174.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_176.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_178.png)

---

![](img/6e5d51dd66a2cde6b882038389bd2645_180.png)

![](img/6e5d51dd66a2cde6b882038389bd2645_182.png)

本节课中我们一起学习了Rust编程语言的基础核心概念。我们从Rust的简介和安装开始，编写了第一个“Hello World”程序，并学会了使用Cargo工具来管理项目。我们深入探讨了Rust中变量默认不可变的特性，以及如何使用 `mut` 关键字使其可变。接着，我们学习了标量类型（整数、浮点数、布尔值、字符）和复合类型（元组、数组）这两种基本数据类型。最后，我们掌握了控制程序执行流程的关键结构：条件分支 `if` 表达式，以及三种循环（`loop`、`while`、`for`）。理解这些基础知识是后续学习Rust更高级特性（如所有权、借用、结构体和枚举）的坚实基础。