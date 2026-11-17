# 006：生命周期与智能指针

在本节课中，我们将要学习Rust中两个核心且独特的概念：生命周期和智能指针。生命周期是Rust编译器用来跟踪引用有效期的系统，是保证内存安全的关键。智能指针则提供了对堆上数据的灵活管理方式。理解这些概念是掌握Rust所有权系统的关键一步。

![](img/df16baaba13d0da1fc4ef9f4e463a28a_1.png)

![](img/df16baaba13d0da1fc4ef9f4e463a28a_3.png)

## 所有权与借用回顾

![](img/df16baaba13d0da1fc4ef9f4e463a28a_5.png)

上一节我们介绍了所有权和借用的核心规则，本节中我们来看看如何用一张表来总结这些概念。

![](img/df16baaba13d0da1fc4ef9f4e463a28a_7.png)

![](img/df16baaba13d0da1fc4ef9f4e463a28a_9.png)

![](img/df16baaba13d0da1fc4ef9f4e463a28a_11.png)

![](img/df16baaba13d0da1fc4ef9f4e463a28a_13.png)

对于任何非借用的类型 `T`（例如 `String` 或自定义结构体），其规则如下：

![](img/df16baaba13d0da1fc4ef9f4e463a28a_15.png)

![](img/df16baaba13d0da1fc4ef9f4e463a28a_17.png)

![](img/df16baaba13d0da1fc4ef9f4e463a28a_18.png)

![](img/df16baaba13d0da1fc4ef9f4e463a28a_20.png)

*   **拥有类型 (`T`)**：
    *   **要求**：有且仅有一个所有者。
    *   **访问权限**：拥有完整的读写和所有权转移权限。
*   **共享借用 (`&T`)**：
    *   **要求**：同一时间只能存在共享借用，不能与独占借用共存。
    *   **访问权限**：只读。不能修改值，也不能通过它获得所有权。
*   **独占借用 (`&mut T`)**：
    *   **要求**：同一时间只能存在一个独占借用，且不能与任何其他借用共存。
    *   **访问权限**：可读写，但依然不拥有该值。

一个关键点是，通过借用访问嵌套字段时，访问权限会传递。例如，如果你有一个 `Food` 结构体的共享借用，那么你只能获得其内部 `String` 字段的共享借用，而非所有权。

```rust
struct Food { s: String }
let f = Food { s: String::from("hello") };
let fb: &Food = &f; // fb 是 f 的共享借用
let s_ref: &String = &fb.s; // 正确：获得 String 的共享借用
// let s: String = fb.s; // 错误！试图从借用中获得所有权
```

Rust编译器会在你违反这些规则时给出明确的错误提示，这比在运行时发生崩溃要安全得多。

![](img/df16baaba13d0da1fc4ef9f4e463a28a_22.png)

![](img/df16baaba13d0da1fc4ef9f4e463a28a_24.png)

## 切片：统一访问连续数据

我们之前遇到了一个问题：编写一个函数时，是应该接收 `&[i32; 5]`（数组的借用）还是 `&Vec<i32>`（向量的借用）？为了代码的通用性，Rust提供了**切片**。

切片 `[T]` 是对一系列连续元素的引用视图。关键点在于，切片类型 `[T]` 本身是**非固定大小类型**。这意味着你不能直接将其用作变量类型或函数参数。

解决方案是增加一层**间接性**，通常通过引用实现：`&[T]` 或 `&mut [T]`。一个 `&[T]` 在底层实际上包含一个指向数据的指针和一个表示长度的值。

切片的美妙之处在于，它可以很容易地从数组或向量创建，并且可以获取子序列。


![](img/df16baaba13d0da1fc4ef9f4e463a28a_26.png)

![](img/df16baaba13d0da1fc4ef9f4e463a28a_27.png)

```rust
let arr = [1, 2, 3, 4, 5];
let vec = vec![1, 2, 3, 4, 5];

// 创建整个数组/向量的切片
let slice_from_arr: &[i32] = &arr[..];
let slice_from_vec: &[i32] = &vec[..];
// 创建子切片 (索引1到3，不包含4)
let sub_slice: &[i32] = &arr[1..4]; // 包含元素 [2, 3, 4]
```

字符串也有类似的对应关系：可增长的 `String` 类型对应只读的字符串切片 `&str`。`&str` 也是一个指针加长度的组合，可以指向 `String` 的一部分或字符串字面量。

![](img/df16baaba13d0da1fc4ef9f4e463a28a_29.png)

![](img/df16baaba13d0da1fc4ef9f4e463a28a_30.png)

![](img/df16baaba13d0da1fc4ef9f4e463a28a_32.png)

利用切片，我们可以编写一个更通用的“获取第一个单词”的函数：

![](img/df16baaba13d0da1fc4ef9f4e463a28a_34.png)

![](img/df16baaba13d0da1fc4ef9f4e463a28a_36.png)

![](img/df16baaba13d0da1fc4ef9f4e463a28a_38.png)

```rust
fn first_word(s: &str) -> &str {
    for (i, &item) in s.as_bytes().iter().enumerate() {
        if item == b' ' {
            return &s[..i];
        }
    }
    &s[..]
}
```

![](img/df16baaba13d0da1fc4ef9f4e463a28a_40.png)

![](img/df16baaba13d0da1fc4ef9f4e463a28a_41.png)

![](img/df16baaba13d0da1fc4ef9f4e463a28a_43.png)

![](img/df16baaba13d0da1fc4ef9f4e463a28a_45.png)

这个函数接收 `&str`，并返回 `&str`，因此它可以处理 `String` 的借用、字符串字面量或任何字符串切片，非常灵活。

## 迭代器方法：`into_iter`, `iter`, `iter_mut`

在拥有借用概念后，我们可以更清晰地理解常见的三种迭代器方法：

*   `into_iter(self)`：消耗集合本身，取得所有权。迭代产生的项是拥有类型 `T`。
*   `iter(&self)`：获取集合的共享借用。迭代产生的项是共享引用 `&T`。
*   `iter_mut(&mut self)`：获取集合的独占借用。迭代产生的项是独占引用 `&mut T`。

选择哪种方法取决于你希望对原始集合和其元素进行何种操作。

## 生命周期：引用能活多久？

Rust编译器通过**生命周期**来跟踪所有引用的有效范围，防止出现悬垂引用。生命周期通常用像 `'a`、`'b` 这样的符号标注。

每个引用都有一个生命周期，即它必须有效的代码区域。编译器（借用检查器）会检查所有生命周期的有效性。核心规则是：**引用的生命周期不能超过其引用的数据的生命周期**。

```rust
{
    let r;                // ---------+-- 'a
    {                     //          |
        let x = 5;        // -+-- 'b |
        r = &x;           //  |       |
    }                     // -+       | // 错误：`x` 的生命周期 'b 太短
    println!("{}", r);    //          |
}                         // ---------+
```

在上面的例子中，引用 `r`（生命周期 `'a`）试图借用 `x`（生命周期 `'b`）。由于 `'b` 没有 `outlive`（存活得比） `'a` 更长，代码无法编译。

![](img/df16baaba13d0da1fc4ef9f4e463a28a_47.png)

![](img/df16baaba13d0da1fc4ef9f4e463a28a_49.png)

![](img/df16baaba13d0da1fc4ef9f4e463a28a_51.png)

![](img/df16baaba13d0da1fc4ef9f4e463a28a_53.png)

## 函数中的生命周期注解

当函数返回一个引用时，编译器有时无法推断出返回引用的生命周期与哪个输入参数相关。这时就需要我们显式地添加**生命周期注解**。

例如，一个返回较长字符串切片的函数：

```rust
fn longest<'a>(x: &'a str, y: &'a str) -> &'a str {
    if x.len() > y.len() {
        x
    } else {
        y
    }
}
```

注解 `<'a>` 声明了一个生命周期参数。`x: &'a str` 和 `y: &'a str` 表示这两个参数和返回的引用 `&'a str` 拥有**相同的生命周期 `'a`**。实际上，`'a` 会被具体化为 `x` 和 `y` 生命周期中**较短的那一个**。这确保了返回的引用总是有效的。

生命周期注解是函数签名的一部分，用于告诉编译器不同参数与返回值之间的生命周期关系。在大多数情况下，编译器可以自动推断（生命周期省略），无需我们手动添加。

![](img/df16baaba13d0da1fc4ef9f4e463a28a_55.png)

![](img/df16baaba13d0da1fc4ef9f4e463a28a_57.png)

![](img/df16baaba13d0da1fc4ef9f4e463a28a_59.png)

## 结构体与枚举中的生命周期

![](img/df16baaba13d0da1fc4ef9f4e463a28a_61.png)

![](img/df16baaba13d0da1fc4ef9f4e463a28a_63.png)

![](img/df16baaba13d0da1fc4ef9f4e463a28a_65.png)

![](img/df16baaba13d0da1fc4ef9f4e463a28a_67.png)

如果结构体或枚举的字段包含引用，那么该类型也必须被赋予一个生命周期参数，以表明该引用有效的时长。

![](img/df16baaba13d0da1fc4ef9f4e463a28a_69.png)

![](img/df16baaba13d0da1fc4ef9f4e463a28a_70.png)

![](img/df16baaba13d0da1fc4ef9f4e463a28a_72.png)


![](img/df16baaba13d0da1fc4ef9f4e463a28a_74.png)

```rust
struct StructWithBorrow<'a> {
    x: &'a str,
}
enum EnumWithBorrow<'a> {
    SomeVariant(&'a str),
}
```

这确保了 `StructWithBorrow` 的实例不会比它内部借用的 `str` 活得更久。

![](img/df16baaba13d0da1fc4ef9f4e463a28a_76.png)

![](img/df16baaba13d0da1fc4ef9f4e463a28a_78.png)

## 智能指针：拥有所有权的指针

有时，我们需要所有权，但又需要将数据存储在堆上，或者需要绕过编译时的大小限制。这时就需要**智能指针**。

![](img/df16baaba13d0da1fc4ef9f4e463a28a_80.png)

![](img/df16baaba13d0da1fc4ef9f4e463a28a_82.png)

![](img/df16baaba13d0da1fc4ef9f4e463a28a_83.png)

![](img/df16baaba13d0da1fc4ef9f4e463a28a_85.png)

![](img/df16baaba13d0da1fc4ef9f4e463a28a_87.png)

*   **`Box<T>`**：最简单的智能指针。它将类型 `T` 的值分配在堆上，而 `Box` 本身（一个指针）存储在栈上。当你拥有 `Box<T>`，你就拥有里面的 `T`。当 `Box` 离开作用域时，堆内存会被自动释放。
    *   **用途**：用于在堆上分配数据；创建递归类型；处理 trait 对象。

![](img/df16baaba13d0da1fc4ef9f4e463a28a_89.png)

![](img/df16baaba13d0da1fc4ef9f4e463a28a_91.png)

*   **`Rc<T>`**：引用计数指针。它允许数据有多个所有者。每次调用 `Rc::clone` 都会增加引用计数，每次 `Rc` 离开作用域则减少计数。当计数为零时，数据被清理。
    *   **限制**：只提供共享（不可变）访问。如果需要有多个所有者且需要可变性，需要配合内部可变性类型（如 `RefCell`）使用。
    *   **注意**：`Rc` 不能用于多线程场景（线程安全版本是 `Arc<T>`）。

![](img/df16baaba13d0da1fc4ef9f4e463a28a_93.png)

![](img/df16baaba13d0da1fc4ef9f4e463a28a_95.png)

*   **`RefCell<T>`**：提供**内部可变性**。它允许你在只有不可变引用的情况下，也能修改其内部的值。这是通过在运行时强制执行借用规则来实现的：如果你试图在已有活跃可变引用时获取另一个可变引用，程序会 `panic`。
    *   **用途**：当你确信代码逻辑是正确的，但 Rust 的编译时借用检查过于保守时使用。它将部分检查从编译时移到了运行时。

## 总结

![](img/df16baaba13d0da1fc4ef9f4e463a28a_97.png)

本节课中我们一起学习了 Rust 中两个高级但至关重要的概念：生命周期和智能指针。

![](img/df16baaba13d0da1fc4ef9f4e463a28a_99.png)

*   **生命周期**是 Rust 保证引用安全的核心机制，它通过编译时检查确保引用不会变成悬垂引用。我们学习了如何阅读生命周期错误，以及如何在函数和结构体中注解生命周期以帮助编译器。
*   **切片** `&[T]` 和 `&str` 是对连续数据的借用视图，它们统一了对数组、向量和字符串的只读或读写访问，提高了代码的通用性。
*   **智能指针**（如 `Box`、`Rc`、`RefCell`）提供了对堆内存管理和特定所有权模式（如多所有权、内部可变性）的支持，是对 Rust 严格所有权系统的有力补充。

![](img/df16baaba13d0da1fc4ef9f4e463a28a_101.png)

![](img/df16baaba13d0da1fc4ef9f4e463a28a_102.png)

理解这些概念是掌握 Rust 内存安全模型的关键。虽然初期可能有些挑战，但随着实践，你会逐渐欣赏它们带来的安全性和表达能力。