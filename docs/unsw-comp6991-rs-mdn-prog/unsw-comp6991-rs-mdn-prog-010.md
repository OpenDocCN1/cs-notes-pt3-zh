# 010：特质对象

![](img/00b06c43e58fb56fa7b5743bd1f63f91_0.png)

![](img/00b06c43e58fb56fa7b5743bd1f63f91_2.png)

![](img/00b06c43e58fb56fa7b5743bd1f63f91_3.png)

## 概述
在本节课中，我们将要学习Rust中一个核心概念：特质对象。我们将从回顾泛型参数和特质的基础知识开始，然后深入探讨如何将特质用作动态类型，以及如何克服在此过程中遇到的各种限制。课程将涵盖特质对象的定义、使用场景、性能权衡以及如何实现自定义迭代器。

---

![](img/00b06c43e58fb56fa7b5743bd1f63f91_5.png)

## 回顾：泛型参数与单态化

![](img/00b06c43e58fb56fa7b5743bd1f63f91_7.png)

上一节我们介绍了泛型类型参数，本节中我们来看看它们是如何在编译时被处理的。

![](img/00b06c43e58fb56fa7b5743bd1f63f91_9.png)

![](img/00b06c43e58fb56fa7b5743bd1f63f91_11.png)

Rust编译器通过一个称为**单态化**的过程来处理泛型。这意味着对于每个被具体类型使用的泛型函数，编译器都会生成一个该类型的专用版本。

例如，对于一个泛型函数 `smallest<T>`，如果它在代码中被用于 `i32`、`f32` 和 `char` 类型，编译器会生成三个独立的函数：`smallest_i32`、`smallest_f32` 和 `smallest_char`。

![](img/00b06c43e58fb56fa7b5743bd1f63f91_13.png)

![](img/00b06c43e58fb56fa7b5743bd1f63f91_15.png)

**核心公式：**
```
单态化：泛型代码 -> 针对每个具体类型的专用代码
```

这种方法的优点是生成的代码运行速度快，可以进行深度优化，是一种**零成本抽象**。缺点是可能会增加编译时间和最终二进制文件的大小。

![](img/00b06c43e58fb56fa7b5743bd1f63f91_17.png)

![](img/00b06c43e58fb56fa7b5743bd1f63f91_18.png)

---

## 探索标准库中的特质

![](img/00b06c43e58fb56fa7b5743bd1f63f91_20.png)

![](img/00b06c43e58fb56fa7b5743bd1f63f91_22.png)

在深入特质对象之前，让我们先熟悉一些Rust标准库中常见的特质。

### `ToString` 和 `Display` 特质
`ToString` 特质用于将值转换为 `String`。它定义了一个方法：
```rust
pub trait ToString {
    fn to_string(&self) -> String;
}
```
许多类型都实现了它。有趣的是，标准库为所有实现了 `Display` 特质的类型**自动提供**了 `ToString` 的实现。

`Display` 特质类似于 `Debug`，但用于用户友好的输出。它使用格式化器，可以避免为最终输出分配大字符串。

![](img/00b06c43e58fb56fa7b5743bd1f63f91_24.png)

![](img/00b06c43e58fb56fa7b5743bd1f63f91_26.png)

### `Clone` 特质
`Clone` 特质允许创建值的副本。它要求实现 `clone` 方法，并提供了一个默认的 `clone_from` 方法。
```rust
pub trait Clone {
    fn clone(&self) -> Self;
    fn clone_from(&mut self, source: &Self) { ... } // 默认实现
}
```
使用 `#[derive(Clone)]` 属性可以自动为结构体生成 `Clone` 实现，前提是所有字段都实现了 `Clone`。

### `Add` 特质
`Add` 特质重载了 `+` 运算符。它使用泛型参数来指定右操作数和返回值的类型。
```rust
pub trait Add<Rhs = Self> {
    type Output;
    fn add(self, rhs: Rhs) -> Self::Output;
}
```
你可以为自定义类型（如 `Point`）实现 `Add` 特质，使其支持加法运算。

![](img/00b06c43e58fb56fa7b5743bd1f63f91_28.png)

![](img/00b06c43e58fb56fa7b5743bd1f63f91_30.png)

### `Iterator` 特质
`Iterator` 特质是Rust迭代功能的核心。它要求定义关联类型 `Item` 和 `next` 方法。
```rust
pub trait Iterator {
    type Item;
    fn next(&mut self) -> Option<Self::Item>;
    // ... 许多有默认实现的方法，如 map, filter, collect
}
```
`IntoIterator` 特质用于可以转换为迭代器的类型（如 `Vec`），而 `FromIterator` 特质则允许从迭代器构建集合（如使用 `collect`）。

![](img/00b06c43e58fb56fa7b5743bd1f63f91_32.png)

![](img/00b06c43e58fb56fa7b5743bd1f63f91_34.png)

![](img/00b06c43e58fb56fa7b5743bd1f63f91_36.png)

![](img/00b06c43e58fb56fa7b5743bd1f63f91_38.png)

---

![](img/00b06c43e58fb56fa7b5743bd1f63f91_40.png)

![](img/00b06c43e58fb56fa7b5743bd1f63f91_42.png)

## 定义和使用自定义特质

现在，让我们通过一个例子来实践如何定义和使用自己的特质。

![](img/00b06c43e58fb56fa7b5743bd1f63f91_44.png)

![](img/00b06c43e58fb56fa7b5743bd1f63f91_46.png)

假设我们有两种动物：`Sheep`（羊）和 `Cow`（牛）。我们定义一个 `Animal` 特质来抽象它们的共同行为。

![](img/00b06c43e58fb56fa7b5743bd1f63f91_48.png)

![](img/00b06c43e58fb56fa7b5743bd1f63f91_50.png)

![](img/00b06c43e58fb56fa7b5743bd1f63f91_52.png)

以下是特质定义和结构体：

![](img/00b06c43e58fb56fa7b5743bd1f63f91_53.png)

```rust
pub trait Animal {
    fn name(&self) -> String;
    fn age(&self) -> u32;
    fn speak(&self) -> String;
    fn say_hello_to<A: Animal>(&self, other: &A) -> String;
}
struct Sheep {
    name: String,
    age: u32,
    at_party: bool,
}

struct Cow {
    name: String,
    age: u32,
    angry: bool,
}
```

接着，我们为 `Sheep` 和 `Cow` 实现 `Animal` 特质。每个实现都需要提供特质中所有方法的定义。

实现后，我们就可以在具体的 `Sheep` 或 `Cow` 实例上调用特质方法了。**需要注意的是，要调用特质方法，该特质必须在当前作用域内**（通常通过 `use` 语句引入）。

![](img/00b06c43e58fb56fa7b5743bd1f63f91_55.png)

![](img/00b06c43e58fb56fa7b5743bd1f63f91_57.png)

我们还可以编写泛型函数，它接受任何实现了 `Animal` 特质的类型：
```rust
fn greet<A: Animal>(animal: &A) {
    println!("{} says {}", animal.name(), animal.speak());
}
```

---

## 特质对象的引入与挑战

上一节我们使用了泛型参数，但有时我们需要在运行时处理多种不同类型的值，并将它们视为同一种东西。例如，我们想要一个包含不同种类动物的 `Vec`。

直觉上，我们可能想写 `Vec<Animal>`，但这会立即遇到问题。

### 问题1：大小未知
Rust需要知道类型的大小来分配内存。`Animal` 是一个特质，不是具体类型，它的大小在编译时无法确定（因为 `Sheep` 和 `Cow` 的大小不同）。

### 解决方案：使用指针
我们可以将特质放在指针后面，指针的大小是固定的。常用的指针是 `Box`（拥有所有权）或引用 `&`（借用）。
```rust
let animals: Vec<Box<dyn Animal>> = vec![
    Box::new(sheep),
    Box::new(cow),
];
```
这里的 `dyn Animal` 就是一个**特质对象**，它表示“任何实现了 `Animal` 特质的类型”。

### 问题2：对象安全性
并非所有特质都可以用作特质对象。我们的 `Animal` 特质目前就不行，因为 `say_hello_to` 方法包含泛型类型参数 `A`。

编译器会报错：*the trait `Animal` cannot be made into an object*。

**为什么？** 特质对象在运行时通过虚表查找方法。如果方法有泛型参数，就需要为每个可能的类型生成一个方法副本，这在运行时无法确定。

### 解决方案A：修改特质方法
将 `say_hello_to` 的参数也改为特质对象，移除泛型参数：
```rust
fn say_hello_to(&self, other: &dyn Animal) -> String;
```

### 解决方案B：使用 `where Self: Sized` 限定
如果某些方法不适用于特质对象，但你又不想把它们从特质中移除，可以使用 `where Self: Sized` 来限定。这意味着该方法只能在编译时知道具体类型的上下文中调用，而不能在特质对象上调用。
```rust
fn say_hello_to<A: Animal>(&self, other: &A) -> String
where
    Self: Sized;
```
这样，`Animal` 特质就可以用作特质对象了，但 `say_hello_to` 方法无法在 `dyn Animal` 上调用。

关于哪些特质和方法是“对象安全”的，具体规则可以参考Rust文档中的 **object safety** 章节。

---

## 性能权衡：单态化 vs 特质对象

现在我们已经看到了两种使用特质的方式，总结一下它们的权衡：

*   **泛型参数（单态化）**：
    *   **编译时**：为每个用到的类型生成专用代码，编译速度可能较慢，二进制文件可能较大。
    *   **运行时**：无动态分发开销，性能最优，可以进行内联等优化。
    *   **适用场景**：性能关键路径，类型在编译时已知。

*   **特质对象（动态分发）**：
    *   **编译时**：只生成一份代码，编译更快，二进制文件更小。
    *   **运行时**：通过虚表进行方法查找，有一次间接调用开销。
    *   **适用场景**：需要存储或处理多种不同类型的集合，类型在运行时才能确定。

---

## 实践：实现迭代器特质

最后，让我们通过实现 `Iterator` 特质来巩固所学知识。我们将实现两个迭代器：一个生成斐波那契数列，另一个迭代 `Vec` 的元素。

### 1. 斐波那契迭代器
```rust
struct Fibonacci {
    current: u32,
    next: u32,
}

impl Iterator for Fibonacci {
    type Item = u32;

    fn next(&mut self) -> Option<Self::Item> {
        let new_next = self.current + self.next;
        self.current = self.next;
        self.next = new_next;
        Some(self.current)
    }
}
```
这个迭代器是无限的，我们可以用 `.take(n)` 来获取前n项。

### 2. Vec迭代器
我们希望创建一个迭代器，可以迭代 `Vec` 的借用切片。
```rust
struct VecIter<'a, T> {
    vec: &'a Vec<T>,
    index: usize,
}

impl<'a, T> Iterator for VecIter<'a, T> {
    type Item = &'a T;

    fn next(&mut self) -> Option<Self::Item> {
        let item = self.vec.get(self.index)?; // 使用 ? 运算符在索引越界时返回 None
        self.index += 1;
        Some(item)
    }
}
```
这里我们使用了生命周期 `'a` 来确保迭代器返回的引用不会比 `Vec` 本身存活得更久。`get` 方法返回 `Option<&T>`，`?` 运算符能很好地处理边界情况。

---

![](img/00b06c43e58fb56fa7b5743bd1f63f91_59.png)

![](img/00b06c43e58fb56fa7b5743bd1f63f91_60.png)

## 总结
本节课中我们一起学习了Rust中强大的**特质对象**概念。我们从回顾泛型和单态化开始，然后探索了标准库中的常见特质。我们定义了自己的 `Animal` 特质，并遇到了将其用作动态类型（特质对象）的挑战，即对象安全性和大小未知问题。我们探讨了使用 `Box<dyn Trait>` 或 `&dyn Trait` 作为解决方案，并分析了泛型（单态化）与特质对象（动态分发）之间的性能权衡。最后，我们通过实现 `Fibonacci` 和 `VecIter` 迭代器，实践了 `Iterator` 特质的用法。掌握这些概念，你将能够更灵活地设计Rust程序，在静态安全性和运行时灵活性之间做出合适的选择。