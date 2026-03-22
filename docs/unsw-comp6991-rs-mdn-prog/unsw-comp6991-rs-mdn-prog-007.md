# 007：集合处理

![](img/3b63af0e858d6dc6e92f83ad721cef04_1.png)

![](img/3b63af0e858d6dc6e92f83ad721cef04_3.png)

![](img/3b63af0e858d6dc6e92f83ad721cef04_5.png)

在本节课中，我们将要学习Rust中的模式匹配、可选值处理以及集合类型（如向量、字符串和哈希映射）的基本操作。我们将通过对比不同编程语言的处理方式，来理解Rust设计哲学的优势。

![](img/3b63af0e858d6dc6e92f83ad721cef04_7.png)

## 模式匹配

上一节我们介绍了控制流，本节中我们来看看Rust中一个非常强大的特性：模式匹配。

模式试图描述数据的形状。例如，`Option<T>`类型的数据形状要么是`Some(T)`，要么是`None`。

我们可以使用`match`表达式来根据数据的形状执行不同的代码分支。`match`表达式是穷尽的，这意味着编译器会强制你处理所有可能的情况。

以下是一个匹配`Option<i32>`的例子：
```rust
let my_option: Option<i32> = Some(100);
match my_option {
    Some(value) => println!("值存在，它是 {}", value),
    None => println!("值是 None"),
}
```
在这个例子中，`value`是一个在匹配到`Some`分支时被绑定的变量。

模式可以嵌套，并且可以使用通配符`_`来匹配任何值但忽略它。`match`本身也是一个表达式，可以返回值。

![](img/3b63af0e858d6dc6e92f83ad721cef04_9.png)

![](img/3b63af0e858d6dc6e92f83ad721cef04_10.png)

以下是使用`match`作为表达式以及使用通配符的例子：
```rust
let expression_value = match my_option {
    Some(42) => 999, // 特殊处理值为42的情况
    Some(_) => 42,   // 匹配任何其他Some值
    None => 0,
};
```

`if let`语法是`match`的一个简洁变体，用于只关心一种模式匹配的情况。

## 可选值对比

![](img/3b63af0e858d6dc6e92f83ad721cef04_12.png)

![](img/3b63af0e858d6dc6e92f83ad721cef04_14.png)

现在，让我们看看不同编程语言如何处理“值可能不存在”的情况，并理解Rust的可选类型设计。

![](img/3b63af0e858d6dc6e92f83ad721cef04_16.png)

在许多语言（如C、Java、Go、Python）中，表示可选值的惯用方式通常依赖于可为空的指针或引用。这要求程序员手动检查值是否为“空”（null、nil、None等），否则可能在运行时导致错误（如空指针异常）。

![](img/3b63af0e858d6dc6e92f83ad721cef04_18.png)

![](img/3b63af0e858d6dc6e92f83ad721cef04_20.png)

![](img/3b63af0e858d6dc6e92f83ad721cef04_22.png)

![](img/3b63af0e858d6dc6e92f83ad721cef04_24.png)

![](img/3b63af0e858d6dc6e92f83ad721cef04_26.png)

Rust使用`Option<T>`枚举来明确表示可选性。一个`Option<T>`的值只能是`Some(T)`或`None`，没有隐式的“空”状态。这通过类型系统将检查从运行时转移到了编译时。

考虑一个从字符串解析整数的函数。在C语言中，你可能需要检查多个输出参数和全局错误变量。在Rust中，函数可以简单地返回`Result<i32, ParseIntError>`或`Option<i32>`，调用者必须通过`match`或类似方法显式处理成功和失败的情况。

这种设计的优势在于：
1.  **编译时保障**：编译器确保你不会意外地使用一个可能不存在的值。
2.  **清晰的意图**：函数签名明确说明了失败的可能性。
3.  **便于重构**：如果函数从“总是成功”变为“可能失败”，需要改变返回类型，这会在所有调用点引发编译错误，迫使你更新处理逻辑。

Tony Hoare将空引用的发明称为“十亿美元的错误”，因为它导致了无数的错误和系统崩溃。Rust的可选类型设计旨在避免这类问题。

当然，为了快速原型开发，Rust也提供了`.unwrap()`或`.expect()`等方法，它们会在值为`None`时使程序崩溃。这些方法就像危险操作的明显标记，当你希望将原型代码强化为生产代码时，可以轻松地找到并替换它们。

## 集合：向量（Vec）

接下来，我们开始学习Rust中最常用的集合类型。首先从向量（`Vec`）开始，它是一种可增长的数据列表。

以下是向量的基本操作：
```rust
let mut v = vec![1, 2, 3]; // 使用宏创建向量
v.push(4);
v.push(5);
println!("向量是: {:?}", v); // 调试打印

![](img/3b63af0e858d6dc6e92f83ad721cef04_28.png)

![](img/3b63af0e858d6dc6e92f83ad721cef04_30.png)

// 索引访问（可能恐慌）
println!("第一个元素: {}", v[0]);

![](img/3b63af0e858d6dc6e92f83ad721cef04_32.png)

![](img/3b63af0e858d6dc6e92f83ad721cef04_34.png)

// 安全索引访问
println!("安全访问第五个元素: {:?}", v.get(4)); // Some(5)
println!("安全访问第十个元素: {:?}", v.get(9)); // None

![](img/3b63af0e858d6dc6e92f83ad721cef04_36.png)

![](img/3b63af0e858d6dc6e92f83ad721cef04_38.png)

// 迭代
for num in &v { // 注意使用引用，避免所有权转移
    println!("{}", num);
}
```

![](img/3b63af0e858d6dc6e92f83ad721cef04_40.png)

![](img/3b63af0e858d6dc6e92f83ad721cef04_42.png)

让我们实现一个计算向量平均值的函数。需要注意处理空向量和整数除法的问题。

![](img/3b63af0e858d6dc6e92f83ad721cef04_44.png)

![](img/3b63af0e858d6dc6e92f83ad721cef04_46.png)

![](img/3b63af0e858d6dc6e92f83ad721cef04_48.png)

![](img/3b63af0e858d6dc6e92f83ad721cef04_50.png)

![](img/3b63af0e858d6dc6e92f83ad721cef04_51.png)

```rust
fn find_mean(numbers: &Vec<i32>) -> Option<f64> {
    if numbers.is_empty() {
        return None;
    }
    let sum: i32 = numbers.iter().sum();
    let length = numbers.len() as f64;
    Some(sum as f64 / length)
}
```

![](img/3b63af0e858d6dc6e92f83ad721cef04_53.png)

![](img/3b63af0e858d6dc6e92f83ad721cef04_55.png)

![](img/3b63af0e858d6dc6e92f83ad721cef04_57.png)

![](img/3b63af0e858d6dc6e92f83ad721cef04_59.png)

![](img/3b63af0e858d6dc6e92f83ad721cef04_61.png)

接着实现一个查找中位数的函数。中位数是将列表排序后位于中间的值。如果列表长度为偶数，则是中间两个数的平均值。

![](img/3b63af0e858d6dc6e92f83ad721cef04_63.png)

```rust
fn find_median(mut numbers: Vec<i32>) -> Option<f64> {
    if numbers.is_empty() {
        return None;
    }
    numbers.sort(); // 原地排序
    let len = numbers.len();
    let middle_index = len / 2;

    if len % 2 == 0 { // 偶数长度
        let lower_middle = numbers[middle_index - 1] as f64;
        let upper_middle = numbers[middle_index] as f64;
        Some((lower_middle + upper_middle) / 2.0)
    } else { // 奇数长度
        Some(numbers[middle_index] as f64)
    }
}
```

## 集合：字符串（String）

Rust中的字符串是UTF-8编码的，可以安全地处理各种语言的字符和表情符号。主要涉及两种类型：`String`（拥有所有权的字符串）和`&str`（字符串切片，通常是借用视图）。

以下是一些基本操作：
```rust
let s1 = "hello"; // &str
let s2 = String::from("world"); // String
let s3 = s1.to_string(); // &str 转 String

// 拼接
let combined = s2 + " " + s1; // 注意：s2的所有权被移动
```

让我们实现一个统计字符串中单词数量的函数，展示函数式编程风格的简洁性。

![](img/3b63af0e858d6dc6e92f83ad721cef04_65.png)

![](img/3b63af0e858d6dc6e92f83ad721cef04_67.png)

```rust
fn word_count(text: &str) -> usize {
    text.split_whitespace().count()
}
```
`split_whitespace()`方法返回一个迭代器，按任意空白字符分割字符串，`count()`方法计算迭代器中的元素数量。

![](img/3b63af0e858d6dc6e92f83ad721cef04_69.png)

![](img/3b63af0e858d6dc6e92f83ad721cef04_71.png)

## 集合：哈希映射（HashMap）

哈希映射存储键值对。要使用自定义类型作为键，该类型必须实现`Eq`和`Hash` trait，通常可以通过`#[derive(PartialEq, Eq, Hash)]`自动派生。

以下是哈希映射的基本用法：
```rust
use std::collections::HashMap;

![](img/3b63af0e858d6dc6e92f83ad721cef04_73.png)

![](img/3b63af0e858d6dc6e92f83ad721cef04_75.png)

#[derive(PartialEq, Eq, Hash)] // 使Student可作为键
struct Student {
    name: String,
    zid: u32,
}

let mut reviews = HashMap::new();
reviews.insert("Adventures of Huckleberry Finn", "My favorite book.");
reviews.insert("Grimms' Fairy Tales", "Masterpiece.");

// 检查键是否存在
if !reviews.contains_key("Les Misérables") {
    println!("We have {} reviews, but Les Misérables ain't one.", reviews.len());
}

// 获取值（返回Option）
let book_review = reviews.get("Grimms' Fairy Tales");

// 遍历
for (book, review) in &reviews {
    println!("{}: {}", book, review);
}
```

## 总结

![](img/3b63af0e858d6dc6e92f83ad721cef04_77.png)

![](img/3b63af0e858d6dc6e92f83ad721cef04_78.png)

本节课中我们一起学习了Rust的核心概念之一——模式匹配，它允许我们根据数据的形状安全地解构和分支代码。我们对比了Rust的`Option`类型与其他语言中处理可选值的方式，理解了其通过类型系统在编译期保障安全的优势。最后，我们初步探索了三种常用的集合类型：向量`Vec`、字符串`String`和哈希映射`HashMap`，并练习了它们的基本操作。在接下来的课程中，我们将更深入地学习迭代器和函数式编程技巧，以便更高效地处理集合数据。