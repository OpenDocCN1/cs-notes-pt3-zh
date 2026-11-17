# 019：将Brainfuck语言实现为宏

![](img/af5f59e7040901394ef4e0eae59f4f7f_1.png)

## 概述

在本节课中，我们将学习如何使用Rust的宏系统，通过创建一个`macro_rules!`宏，将Brainfuck这门极简的图灵完备编程语言实现为一个Rust宏。我们将从零开始，逐步构建一个能够将Brainfuck源代码在编译时转换为等效Rust代码的宏。

## 什么是Brainfuck？🤔

Brainfuck是一种由Urban Müller于1993年创建的深奥编程语言。深奥编程语言通常被设计来测试编程语言设计的边界、作为概念验证、软件艺术、作为其他语言的接口，或者纯粹作为一个玩笑。

![](img/af5f59e7040901394ef4e0eae59f4f7f_3.png)

![](img/af5f59e7040901394ef4e0eae59f4f7f_5.png)

Brainfuck之所以特别，是因为它极其简单，却又是图灵完备的。这意味着理论上，它可以计算任何可计算的问题。这门语言只有八个命令，每个命令由一个字符表示。

![](img/af5f59e7040901394ef4e0eae59f4f7f_7.png)

### Brainfuck的八个命令

![](img/af5f59e7040901394ef4e0eae59f4f7f_9.png)

以下是Brainfuck的八个命令及其含义。Brainfuck程序操作一个字节数组（通常称为“纸带”）和一个指向该数组当前位置的“数据指针”。初始时，所有字节通常为零。

![](img/af5f59e7040901394ef4e0eae59f4f7f_11.png)

1.  **`>`**：将数据指针向右移动一个单元格。
2.  **`<`**：将数据指针向左移动一个单元格。
3.  **`+`**：将数据指针当前指向的字节值加一（通常使用环绕加法，例如 `255 + 1 = 0`）。
4.  **`-`**：将数据指针当前指向的字节值减一（通常使用环绕减法，例如 `0 - 1 = 255`）。
5.  **`.`**：输出数据指针当前指向的字节值对应的ASCII字符。
6.  **`,`**：从输入读取一个字节，并将其ASCII值存储到数据指针当前指向的单元格。
7.  **`[`**：如果数据指针当前指向的字节值为零，则跳转到与之匹配的 `]` 之后；否则，继续执行下一条指令。这相当于一个 `while` 循环的开始。
8.  **`]`**：无条件跳转回与之匹配的 `[` 处，以重新检查循环条件。

![](img/af5f59e7040901394ef4e0eae59f4f7f_13.png)

![](img/af5f59e7040901394ef4e0eae59f4f7f_15.png)

## Rust宏基础 🛠️

上一节我们介绍了Brainfuck语言，本节中我们来看看Rust宏的基本概念。宏是Rust中强大的元编程工具，它本质上是一个在编译时运行的函数，接收源代码作为输入，并生成新的源代码作为输出。

### 宏的声明与使用

声明一个简单的`macro_rules!`宏的语法如下：
```rust
macro_rules! macro_name {
    ( /* 模式 */ ) => { /* 展开的代码 */ };
}
```
宏可以通过 `!` 调用，例如 `println!` 和 `vec!`。

### 捕获与重复

在宏的模式中，我们可以使用特殊的捕获语法来匹配不同类型的代码片段，例如表达式 `$expr:expr`。我们还可以使用重复语法来处理可变数量的输入。

以下是重复语法的基本形式：
```
$ ( /* 要重复的模式 */ ) 分隔符 重复操作符
```
-   **分隔符**：通常是 `,` 或 `;`，用于分隔重复项。
-   **重复操作符**：
    -   `*`：零次或多次。
    -   `+`：一次或多次。
    -   `?`：零次或一次。

在宏的展开部分，使用 `$( ... )*` 来对捕获的内容进行重复展开。

### 一个简单的例子：DIY `vec!` 宏

为了理解宏的工作原理，让我们先创建一个简化版的 `vec!` 宏。

```rust
macro_rules! diy_vec {
    ( $( $elem:expr ),* $(,)? ) => {{
        let mut temp_vec = Vec::new();
        $(
            temp_vec.push($elem);
        )*
        temp_vec
    }};
}
```
这个宏匹配一个由逗号分隔的表达式列表（允许末尾有一个可选的逗号）。它展开的代码会创建一个临时的可变向量，将每个表达式推入向量，最后返回这个向量。

## 构建Brainfuck宏 🧠

现在我们已经掌握了宏的基础知识，可以开始构建我们的Brainfuck宏了。我们的目标是创建一个名为 `bf!` 的宏，它接收Brainfuck源代码，并将其转换为在运行时执行相同逻辑的Rust代码。

### 核心策略：递归TT吞噬

![](img/af5f59e7040901394ef4e0eae59f4f7f_17.png)

我们将使用一种称为“递归TT吞噬”的技术。TT代表“Token Tree”（词法树）。基本思想是：宏将逐个“吞噬”输入令牌，为每个Brainfuck命令生成一小段Rust代码，然后递归地调用自身来处理剩余的令牌。

### 宏的结构设计

我们的宏需要维护两个状态：纸带（字节数组）和数据指针（索引）。我们将把它们作为参数传递给宏的递归调用。



宏的顶层规则将匹配纯Brainfuck代码，初始化状态，然后进入递归处理。



```rust
macro_rules! bf {
    // 顶层规则：接收纯Brainfuck代码
    ( $($code:tt)* ) => {{
        let mut __tape = vec![0u8; 2048];
        let mut __ptr = 1024; // 从中间开始
        bf!(@inner __tape, __ptr, $($code)*);
    }};
    // 内部递归规则
    (@inner $tape:ident, $ptr:ident, ) => {}; // 没有更多指令，结束
    // 处理各个Brainfuck命令的规则...
}
```

### 实现各个命令

接下来，我们为每个Brainfuck命令实现一条规则。每条规则匹配特定的命令令牌，生成对应的Rust代码，然后递归调用宏自身处理剩余部分。

以下是处理 `>`、`<`、`+`、`-` 命令的规则：

```rust
    // 向右移动指针
    (@inner $tape:ident, $ptr:ident, > $($rest:tt)*) => {
        $ptr += 1;
        bf!(@inner $tape, $ptr, $($rest)*);
    };
    // 向左移动指针
    (@inner $tape:ident, $ptr:ident, < $($rest:tt)*) => {
        $ptr -= 1;
        bf!(@inner $tape, $ptr, $($rest)*);
    };
    // 递增当前字节（使用环绕加法）
    (@inner $tape:ident, $ptr:ident, + $($rest:tt)*) => {
        $tape[$ptr] = $tape[$ptr].wrapping_add(1);
        bf!(@inner $tape, $ptr, $($rest)*);
    };
    // 递减当前字节（使用环绕减法）
    (@inner $tape:ident, $ptr:ident, - $($rest:tt)*) => {
        $tape[$ptr] = $tape[$ptr].wrapping_sub(1);
        bf!(@inner $tape, $ptr, $($rest)*);
    };
```

### 处理输入/输出

处理输入（`,`）和输出（`.`）需要与Rust的IO系统交互。

```rust
    // 输出当前字节
    (@inner $tape:ident, $ptr:ident, . $($rest:tt)*) => {
        print!("{}", $tape[$ptr] as char);
        std::io::Write::flush(&mut std::io::stdout()).unwrap();
        bf!(@inner $tape, $ptr, $($rest)*);
    };
    // 输入一个字节
    (@inner $tape:ident, $ptr:ident, , $($rest:tt)*) => {
        let mut input = [0u8; 1];
        std::io::Read::read(&mut std::io::stdin(), &mut input).unwrap();
        $tape[$ptr] = input[0];
        bf!(@inner $tape, $ptr, $($rest)*);
    };
```

### 实现循环

循环（`[` 和 `]`）是Brainfuck中最有趣的部分。得益于Rust宏要求括号必须平衡的特性，我们可以轻松匹配整个循环体。

![](img/af5f59e7040901394ef4e0eae59f4f7f_27.png)

![](img/af5f59e7040901394ef4e0eae59f4f7f_29.png)

```rust
    // 循环开始
    (@inner $tape:ident, $ptr:ident, [ $($body:tt)* ] $($rest:tt)*) => {
        while $tape[$ptr] != 0 {
            bf!(@inner $tape, $ptr, $($body)*);
        }
        bf!(@inner $tape, $ptr, $($rest)*);
    };
```
这条规则匹配一个左括号 `[`，然后捕获直到匹配的右括号 `]` 之间的所有令牌作为循环体 `$body`。它展开为一个Rust的 `while` 循环，只要当前字节不为零，就执行循环体内的Brainfuck代码。循环结束后，继续处理剩余的令牌。

![](img/af5f59e7040901394ef4e0eae59f4f7f_31.png)

![](img/af5f59e7040901394ef4e0eae59f4f7f_33.png)

### 处理令牌边界情况

由于Rust的词法分析器会将 `>>` 解析为单个“右移”令牌，而不是两个 `>`，我们需要添加额外规则来处理这种边界情况。

![](img/af5f59e7040901394ef4e0eae59f4f7f_35.png)

![](img/af5f59e7040901394ef4e0eae59f4f7f_36.png)

```rust
    // 处理 `>>` 被识别为右移的情况
    (@inner $tape:ident, $ptr:ident, >> $($rest:tt)*) => {
        bf!(@inner $tape, $ptr, > > $($rest)*);
    };
    // 类似地处理 `<<`
    (@inner $tape:ident, $ptr:ident, << $($rest:tt)*) => {
        bf!(@inner $tape, $ptr, < < $($rest)*);
    };
```
这些规则将复合令牌“分解”为单个命令，然后重新调用宏。

![](img/af5f59e7040901394ef4e0eae59f4f7f_38.png)

![](img/af5f59e7040901394ef4e0eae59f4f7f_40.png)

## 使用Brainfuck宏 🚀

![](img/af5f59e7040901394ef4e0eae59f4f7f_42.png)

现在，我们的宏已经完成！让我们用它来运行一些Brainfuck程序。

![](img/af5f59e7040901394ef4e0eae59f4f7f_44.png)

![](img/af5f59e7040901394ef4e0eae59f4f7f_46.png)

### Hello World

![](img/af5f59e7040901394ef4e0eae59f4f7f_48.png)

最经典的例子：打印“Hello World”。

```rust
bf!(
    ++++++++[>++++[>++>+++>+++>+<<<<-]>+>+>->>+[<]<-]>>.>---.+++++++..+++.>>.<-.<.+++.------.--------.>>+.>++.
);
```
运行此Rust程序，将在终端输出“Hello World!”。

### ROT13 加密/解密

ROT13是一种简单的字母替换密码。以下Brainfuck程序实现了一个ROT13密码器。

```rust
bf!(
    // ... (很长的ROT13 Brainfuck代码)
);
```
运行后，输入文本，程序会输出其ROT13加密/解密的结果。

### 计算数学常数 e

![](img/af5f59e7040901394ef4e0eae59f4f7f_50.png)

![](img/af5f59e7040901394ef4e0eae59f4f7f_52.png)

这个Brainfuck程序可以计算并输出数学常数 e 的十进制数字。

![](img/af5f59e7040901394ef4e0eae59f4f7f_54.png)

```rust
#![recursion_limit = "1024"] // 需要提高递归限制
bf!(
    // ... (非常长的计算e的Brainfuck代码)
);
```
由于该程序嵌套循环极深，导致宏递归展开次数超过默认限制（128），我们需要使用 `#![recursion_limit = “1024”]` 属性来提高编译器的递归限制。

![](img/af5f59e7040901394ef4e0eae59f4f7f_56.png)

### Brainfuck解释器（元循环）

![](img/af5f59e7040901394ef4e0eae59f4f7f_58.png)

最令人惊叹的例子：一个用Brainfuck编写的Brainfuck解释器。我们可以用我们的 `bf!` 宏来运行这个解释器，然后让这个解释器再去执行其他的Brainfuck程序（例如Hello World）。

![](img/af5f59e7040901394ef4e0eae59f4f7f_60.png)

```rust
bf!(
    // ... (极其冗长的Brainfuck解释器源代码)
);
```
运行此程序，然后将Hello World的Brainfuck代码（以`!`结尾）输入给这个解释器，你将看到它最终输出“Hello World”。这实现了宏的“自举”——用我们的宏运行一个能理解Brainfuck的Brainfrick程序。

![](img/af5f59e7040901394ef4e0eae59f4f7f_62.png)

![](img/af5f59e7040901394ef4e0eae59f4f7f_64.png)

## 总结

本节课中我们一起学习了：
1.  **Brainfuck语言**：一门只有八个命令、极简却图灵完备的深奥编程语言。
2.  **Rust宏**：`macro_rules!` 宏的基础，包括捕获、重复和递归。
3.  **递归TT吞噬**：一种构建复杂宏的技术，通过递归调用逐步处理输入令牌。
4.  **Brainfuck宏的实现**：我们逐步构建了一个 `bf!` 宏，它能将Brainfuck源代码在编译时转换为等效的Rust代码，实现了从Brainfuck到Rust的转译。
5.  **宏的强大能力**：通过这个练习，我们看到了宏如何能够将一种语言的语义嵌入到Rust中，并在编译时执行复杂的代码生成任务，展示了元编程的威力。

![](img/af5f59e7040901394ef4e0eae59f4f7f_66.png)

最终完成的宏是一个将Brainfuck语言嵌入Rust的完整、可用的转译器，它生动地演示了Rust宏系统的灵活性和强大功能。