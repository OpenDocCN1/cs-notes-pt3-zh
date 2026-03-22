# 012：函数与闭包 🦀

![](img/faca3d266a1f263ca20b61e3a71efe74_1.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_3.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_5.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_7.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_9.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_11.png)

在本节课中，我们将要学习Rust中函数与闭包的核心概念。我们将从基础的函数指针开始，逐步深入到闭包及其环境捕获机制，并探讨三种关键的函数特质（`Fn`、`FnMut`、`FnOnce`）及其与所有权系统的深刻联系。最后，我们将通过重构一个自定义的`map`函数来应用这些知识。

![](img/faca3d266a1f263ca20b61e3a71efe74_13.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_15.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_17.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_18.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_20.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_22.png)

## 函数指针

![](img/faca3d266a1f263ca20b61e3a71efe74_24.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_26.png)

上一节我们介绍了课程概述，本节中我们来看看函数指针。函数指针允许我们将函数作为值来传递和使用，这是将函数视为“一等公民”的基础。

![](img/faca3d266a1f263ca20b61e3a71efe74_28.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_29.png)

函数指针的类型语法如下：
```rust
fn(i32, i32) -> i32
```
这表示一个接收两个`i32`参数并返回一个`i32`的函数。

以下是如何使用函数指针的示例：
```rust
fn add(x: i32, y: i32) -> i32 {
    x + y
}

fn main() {
    let my_thing: fn(i32, i32) -> i32 = add;
    println!("2 + 2 = {}", my_thing(2, 2)); // 输出：2 + 2 = 4
}
```

## 闭包与环境捕获

上一节我们介绍了函数指针，本节中我们来看看闭包。闭包是函数指针的扩展，它可以捕获并访问其定义环境中的变量。

闭包使用`||`语法定义，其具体类型由编译器自动生成且无法显式命名。
```rust
let factor = 2.5;
let closure = |x: i32| -> f32 { x as f32 * std::f32::consts::PI * factor };
```

![](img/faca3d266a1f263ca20b61e3a71efe74_31.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_32.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_34.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_36.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_38.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_39.png)

当闭包捕获环境变量时，它就不再是简单的函数指针。为了处理这种未知的具体类型，Rust提供了函数特质。

![](img/faca3d266a1f263ca20b61e3a71efe74_41.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_43.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_45.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_47.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_49.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_50.png)

## 函数特质：`Fn`、`FnMut`、`FnOnce`

![](img/faca3d266a1f263ca20b61e3a71efe74_52.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_54.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_56.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_57.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_59.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_61.png)

上一节我们看到了闭包如何捕获环境，本节中我们来看看描述闭包行为的三种特质。这些特质定义了调用闭包所需的所有权权限。

![](img/faca3d266a1f263ca20b61e3a71efe74_63.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_65.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_67.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_68.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_70.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_72.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_74.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_76.png)

以下是三种函数特质的核心区别：
1.  **`FnOnce`**: 闭包可以**被调用一次**。它可能获取其捕获变量的所有权（对应`self`）。
2.  **`FnMut`**: 闭包可以**被多次调用，但不能并发调用**。它可能可变地借用其捕获的变量（对应`&mut self`）。
3.  **`Fn`**: 闭包可以**被多次且并发地调用**。它只能不可变地借用其捕获的变量（对应`&self``）。

所有闭包都至少实现`FnOnce`。仅捕获不可变引用的闭包也实现`Fn`。捕获可变引用但不获取所有权的闭包实现`FnMut`。

## 重构 `my_map` 函数

上一节我们理解了函数特质，本节中我们将应用这些知识来改进我们的`my_map`函数，使其能够接受闭包。

最初，我们的`my_map`函数签名使用函数指针，这限制了它只能使用不捕获环境的函数。
```rust
fn my_map<I, CurrentItem, NewItem>(iter: I, func: fn(CurrentItem) -> NewItem) -> MyMap<I, CurrentItem, NewItem>
where
    I: Iterator<Item = CurrentItem>,
{
    MyMap { iter, func }
}
```

为了支持闭包，我们需要使用泛型和特质绑定。我们将参数`func`的类型改为泛型`F`，并要求`F`实现`FnMut`特质（因为`map`需要多次调用该函数）。
```rust
fn my_map<I, F, NewItem>(iter: I, func: F) -> MyMap<I, F, NewItem>
where
    I: Iterator,
    F: FnMut(I::Item) -> NewItem, // 使用 FnMut 特质
{
    MyMap { iter, func }
}
```

![](img/faca3d266a1f263ca20b61e3a71efe74_78.png)

对应的`MyMap`结构体和迭代器实现也需要更新泛型参数。
```rust
struct MyMap<I, F, NewItem> {
    iter: I,
    func: F,
}

![](img/faca3d266a1f263ca20b61e3a71efe74_80.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_82.png)

impl<I, F, NewItem> Iterator for MyMap<I, F, NewItem>
where
    I: Iterator,
    F: FnMut(I::Item) -> NewItem, // 迭代时也需要 FnMut
{
    type Item = NewItem;

    fn next(&mut self) -> Option<Self::Item> {
        let current_item = self.iter.next()?;
        Some((self.func)(current_item)) // 调用闭包
    }
}
```

![](img/faca3d266a1f263ca20b61e3a71efe74_84.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_86.png)

现在，我们的`my_map`可以处理可变捕获的闭包了。
```rust
let mut counter = 0;
let result: Vec<_> = my_map(vec![1, 2, 3].into_iter(), |x| {
    counter += 1; // 闭包可变地捕获了 counter
    x * counter
}).collect();
assert_eq!(result, vec![1, 4, 9]); // 1*1, 2*2, 3*3
```

![](img/faca3d266a1f263ca20b61e3a71efe74_88.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_89.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_91.png)

## API 设计考量

![](img/faca3d266a1f263ca20b61e3a71efe74_93.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_95.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_96.png)

上一节我们成功使`my_map`支持了闭包，本节中我们来探讨一下API设计的最佳实践。选择使用哪种函数特质（`FnOnce`、`FnMut`、`Fn`）是一种权衡。

![](img/faca3d266a1f263ca20b61e3a71efe74_98.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_100.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_102.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_103.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_105.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_107.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_109.png)

选择特质的原则如下：
*   **尽可能使用限制最少的特质**：这为调用者提供了最大的灵活性。例如，如果函数只需被调用一次，优先考虑`FnOnce`。
*   **根据需求向右移动**：如果API需要调用函数多次，则需使用`FnMut`。如果需要并发调用，则必须使用`Fn`。
*   **平衡双方需求**：API设计者希望给自己最大的灵活性（倾向于`Fn`），而API调用者希望有最大的表达能力（倾向于`FnOnce`）。需要在两者间找到平衡点。

![](img/faca3d266a1f263ca20b61e3a71efe74_111.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_112.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_114.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_116.png)

对于我们的`my_map`，因为迭代器的`next`方法需要多次调用闭包，所以`FnMut`是正确的选择。

![](img/faca3d266a1f263ca20b61e3a71efe74_118.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_120.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_122.png)

## 示例：计时函数

![](img/faca3d266a1f263ca20b61e3a71efe74_124.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_125.png)

最后，我们来看一个使用`FnOnce`的实用示例：一个测量任何闭包执行时间的通用函数。
```rust
use std::time::{Instant, Duration};

fn time_closure<F, T>(closure: F) -> (T, Duration)
where
    F: FnOnce() -> T, // 只需调用一次，使用 FnOnce
{
    let start = Instant::now();
    let result = closure();
    let duration = start.elapsed();
    (result, duration)
}

![](img/faca3d266a1f263ca20b61e3a71efe74_127.png)

fn main() {
    let (answer, time_taken) = time_closure(|| {
        // 模拟一些工作
        std::thread::sleep(std::time::Duration::from_millis(100));
        42
    });
    println!("闭包返回了 {}，耗时 {:?}", answer, time_taken);
}
```

![](img/faca3d266a1f263ca20b61e3a71efe74_129.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_131.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_133.png)

## 总结

![](img/faca3d266a1f263ca20b61e3a71efe74_135.png)

![](img/faca3d266a1f263ca20b61e3a71efe74_136.png)

本节课中我们一起学习了Rust中函数与闭包的核心机制。我们从函数指针开始，了解了闭包如何捕获环境变量，并深入探讨了`Fn`、`FnMut`、`FnOnce`三种函数特质及其与所有权系统（`&self`、`&mut self`、`self`）的对应关系。我们应用这些知识重构了`my_map`函数，使其能够支持更灵活的闭包操作，并讨论了在API设计中如何权衡选择不同的函数特质。理解这些概念是掌握Rust函数式编程和后续学习并发编程的重要基础。