# 003：集合与迭代器

## 概述

在本节课中，我们将学习Rust中的核心概念：集合与迭代器。我们将探讨如何使用向量（Vec）、数组等集合类型，并深入了解迭代器（Iterator）这一强大的抽象，它允许我们以声明式和函数式风格处理数据序列。

![](img/9dca300d6d3c6b004c51be19d552dcdd_1.png)

---

![](img/9dca300d6d3c6b004c51be19d552dcdd_3.png)

![](img/9dca300d6d3c6b004c51be19d552dcdd_5.png)

## 集合简介

![](img/9dca300d6d3c6b004c51be19d552dcdd_7.png)

我们已经见过数组（Array），它是一种固定大小的集合。例如：
```rust
let my_array = [1, 2, 3];
```
数组必须始终包含固定数量的元素，其类型为 `[i32; 3]`。

![](img/9dca300d6d3c6b004c51be19d552dcdd_9.png)

![](img/9dca300d6d3c6b004c51be19d552dcdd_11.png)

![](img/9dca300d6d3c6b004c51be19d552dcdd_13.png)

向量（Vec）则提供了动态大小的集合。例如：
```rust
let my_vec = vec![1, 2, 3];
```
向量可以增长和收缩，其类型为 `Vec<i32>`。

![](img/9dca300d6d3c6b004c51be19d552dcdd_15.png)

![](img/9dca300d6d3c6b004c51be19d552dcdd_16.png)

![](img/9dca300d6d3c6b004c51be19d552dcdd_18.png)

![](img/9dca300d6d3c6b004c51be19d552dcdd_20.png)

![](img/9dca300d6d3c6b004c51be19d552dcdd_22.png)

![](img/9dca300d6d3c6b004c51be19d552dcdd_23.png)

![](img/9dca300d6d3c6b004c51be19d552dcdd_24.png)

![](img/9dca300d6d3c6b004c51be19d552dcdd_26.png)

![](img/9dca300d6d3c6b004c51be19d552dcdd_28.png)

向量与数组的一个关键区别在于，向量将其数据存储在堆（Heap）上，而数组通常存储在栈（Stack）上。这使得向量更适合存储大量数据或需要动态调整大小的场景。

![](img/9dca300d6d3c6b004c51be19d552dcdd_30.png)

---

![](img/9dca300d6d3c6b004c51be19d552dcdd_32.png)

## 向量的动态特性

![](img/9dca300d6d3c6b004c51be19d552dcdd_34.png)

向量支持动态调整大小。我们可以向向量中添加或移除元素。

以下是向向量添加元素的方法：
```rust
let mut my_vec = vec![1, 2, 3];
my_vec.push(4);
```

要从向量中移除元素，可以使用 `remove` 方法：
```rust
my_vec.remove(2); // 移除索引为2的元素
```

向量包含三个关键信息：元素本身、当前长度（length）和容量（capacity）。容量是为未来元素预分配的空间，以避免频繁的内存重新分配。

为了提高性能，可以使用 `Vec::with_capacity` 预先分配足够的空间：
```rust
let mut doubled_vec = Vec::with_capacity(input_vec.len());
```

![](img/9dca300d6d3c6b004c51be19d552dcdd_36.png)

![](img/9dca300d6d3c6b004c51be19d552dcdd_37.png)

---

## 迭代器（Iterator）简介

迭代器是Rust中处理序列数据的核心抽象。任何实现了 `Iterator` trait 的类型都可以被迭代。

迭代器的核心方法是 `next`，它返回一个 `Option<T>`。当序列中还有元素时，返回 `Some(element)`；当序列耗尽时，返回 `None`。

以下是如何从向量创建迭代器：
```rust
let my_vec = vec![1, 2, 3];
let mut iter = my_vec.into_iter();
println!("{:?}", iter.next()); // Some(1)
println!("{:?}", iter.next()); // Some(2)
println!("{:?}", iter.next()); // Some(3)
println!("{:?}", iter.next()); // None
```

![](img/9dca300d6d3c6b004c51be19d552dcdd_39.png)

![](img/9dca300d6d3c6b004c51be19d552dcdd_40.png)

![](img/9dca300d6d3c6b004c51be19d552dcdd_42.png)

迭代器的一个主要优势是它抽象了底层数据结构的细节，为各种集合提供了统一的处理接口。

---

![](img/9dca300d6d3c6b004c51be19d552dcdd_44.png)

## 迭代器适配器与方法

![](img/9dca300d6d3c6b004c51be19d552dcdd_46.png)

![](img/9dca300d6d3c6b004c51be19d552dcdd_48.png)

![](img/9dca300d6d3c6b004c51be19d552dcdd_49.png)

迭代器提供了许多强大的适配器方法，允许我们以函数式风格转换和组合数据。

![](img/9dca300d6d3c6b004c51be19d552dcdd_51.png)

![](img/9dca300d6d3c6b004c51be19d552dcdd_53.png)

以下是一些常用的迭代器方法：

*   **`map`**：对每个元素应用一个函数，将其转换为另一种类型。
    ```rust
    let doubled: Vec<_> = vec![1, 2, 3].into_iter().map(|x| x * 2).collect();
    // 结果为 [2, 4, 6]
    ```

*   **`filter`**：只保留满足条件的元素。
    ```rust
    let positives: Vec<_> = vec![-1, 0, 1, 2].into_iter().filter(|&x| x > 0).collect();
    // 结果为 [1, 2]
    ```

![](img/9dca300d6d3c6b004c51be19d552dcdd_55.png)

![](img/9dca300d6d3c6b004c51be19d552dcdd_57.png)

*   **`zip`**：将两个迭代器“压缩”成一个迭代器，产生元素对。
    ```rust
    let a1 = vec![1, 2, 3];
    let a2 = vec![4, 5, 6];
    let zipped: Vec<_> = a1.into_iter().zip(a2.into_iter()).collect();
    // 结果为 [(1, 4), (2, 5), (3, 6)]
    ```

![](img/9dca300d6d3c6b004c51be19d552dcdd_59.png)

![](img/9dca300d6d3c6b004c51be19d552dcdd_60.png)

*   **`fold`**：将一个序列“折叠”成单个值。它接受一个初始值和一个闭包，闭包将当前累积值和下一个元素作为输入，返回新的累积值。
    ```rust
    let sum = vec![1, 2, 3, 4].into_iter().fold(0, |acc, x| acc + x);
    // 结果为 10
    ```

![](img/9dca300d6d3c6b004c51be19d552dcdd_62.png)

![](img/9dca300d6d3c6b004c51be19d552dcdd_64.png)

![](img/9dca300d6d3c6b004c51be19d552dcdd_66.png)

![](img/9dca300d6d3c6b004c51be19d552dcdd_68.png)

![](img/9dca300d6d3c6b004c51be19d552dcdd_70.png)

---

## 实践示例：计算平均值

上一节我们介绍了迭代器的基本概念和常用方法，本节中我们来看看如何应用它们解决实际问题。

![](img/9dca300d6d3c6b004c51be19d552dcdd_72.png)

![](img/9dca300d6d3c6b004c51be19d552dcdd_73.png)

![](img/9dca300d6d3c6b004c51be19d552dcdd_74.png)

![](img/9dca300d6d3c6b004c51be19d552dcdd_76.png)

让我们编写一个函数来计算一个整数向量的平均值（均值）。

首先，考虑函数签名。由于向量可能为空，且平均值可能是小数，我们返回一个 `Option<f64>`。

以下是使用迭代器的函数式实现：
```rust
fn mean_functional(numbers: Vec<i32>) -> Option<f64> {
    if numbers.is_empty() {
        return None;
    }
    let sum: i32 = numbers.iter().sum();
    Some(sum as f64 / numbers.len() as f64)
}
```

这个实现简洁明了，利用了迭代器的 `sum` 方法。

---

## 实践示例：查找最长相等子序列

接下来，我们解决一个更复杂的问题：给定两个向量，找出它们对应位置上连续相等元素的最长子序列长度。

例如，对于向量 `[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]` 和 `[1, 0, 3, 4, 5, 6, 20, 8, 9, 10]`，最长相等子序列是 `[3, 4, 5, 6]`，长度为4。

以下是结合迭代器适配器的解决方案：
```rust
fn longest_equal_run_functional(x: Vec<i32>, y: Vec<i32>) -> usize {
    x.into_iter()
        .zip(y.into_iter())
        .map(|(xe, ye)| xe == ye)
        .fold((0, 0), |(best, current), equal| {
            if equal {
                let new_current = current + 1;
                (best.max(new_current), new_current)
            } else {
                (best, 0)
            }
        })
        .0
}
```
这个实现使用了 `zip` 来配对元素，`map` 来比较是否相等（生成布尔序列），最后用 `fold` 来跟踪当前运行长度和最佳长度。

---

## 哈希映射（HashMap）简介

![](img/9dca300d6d3c6b004c51be19d552dcdd_78.png)

![](img/9dca300d6d3c6b004c51be19d552dcdd_79.png)

哈希映射是存储键值对的集合。它在Rust中非常常用，通常通过 `std::collections::HashMap` 使用。

以下是如何使用哈希映射来统计一个向量中每个元素出现的次数（频率）：
```rust
use std::collections::HashMap;

fn frequency_map(numbers: Vec<i32>) -> HashMap<i32, i32> {
    let mut map = HashMap::new();
    for &num in &numbers {
        *map.entry(num).or_insert(0) += 1;
    }
    map
}
```
这里使用了 `entry` API，它提供了一种高效的方式来检查键是否存在并插入或更新值。

---

## 实践示例：查找众数（Mode）

![](img/9dca300d6d3c6b004c51be19d552dcdd_81.png)

最后，我们使用哈希映射来查找一个向量中的众数（出现次数最多的元素）。

![](img/9dca300d6d3c6b004c51be19d552dcdd_83.png)

![](img/9dca300d6d3c6b004c51be19d552dcdd_85.png)

![](img/9dca300d6d3c6b004c51be19d552dcdd_87.png)

以下是实现：
```rust
fn mode(numbers: Vec<i32>) -> Option<i32> {
    let mut frequency = HashMap::new();
    for &num in &numbers {
        *frequency.entry(num).or_insert(0) += 1;
    }
    frequency
        .into_iter()
        .max_by_key(|&(_, count)| count)
        .map(|(value, _)| value)
}
```
这个函数首先构建频率映射，然后使用迭代器的 `max_by_key` 方法找到计数最大的条目，最后使用 `map` 提取出该元素的值。如果向量为空，`max_by_key` 返回 `None`，函数也相应返回 `None`。

![](img/9dca300d6d3c6b004c51be19d552dcdd_89.png)

![](img/9dca300d6d3c6b004c51be19d552dcdd_91.png)

![](img/9dca300d6d3c6b004c51be19d552dcdd_93.png)

---

## 字符串作为字符集合

字符串（`String`）在Rust中也可以被视为集合。由于Rust字符串是UTF-8编码的，直接索引字节可能得不到预期的字符。通常，我们使用 `chars` 方法来获取字符迭代器。

![](img/9dca300d6d3c6b004c51be19d552dcdd_95.png)

![](img/9dca300d6d3c6b004c51be19d552dcdd_97.png)

以下是遍历字符串字符的方法：
```rust
let s = String::from("Hello 🦀");
for ch in s.chars() {
    println!("{}", ch);
}
// 输出： H, e, l, l, o, 空格, 🦀
```

---

## 总结

本节课中我们一起学习了Rust中集合与迭代器的核心知识。

![](img/9dca300d6d3c6b004c51be19d552dcdd_99.png)

![](img/9dca300d6d3c6b004c51be19d552dcdd_101.png)

我们探讨了向量（`Vec`）的动态特性及其与数组的区别，深入了解了迭代器（`Iterator`）这一强大抽象，它通过 `next` 方法提供了处理序列的统一接口。我们实践了多种迭代器适配器，如 `map`、`filter`、`zip` 和 `fold`，并使用它们以函数式风格解决了计算平均值、查找最长相等子序列等问题。最后，我们介绍了哈希映射（`HashMap`）的基本用法，并用它来查找数据中的众数。



![](img/9dca300d6d3c6b004c51be19d552dcdd_107.png)

![](img/9dca300d6d3c6b004c51be19d552dcdd_109.png)

掌握这些概念对于编写高效、地道的Rust代码至关重要。迭代器不仅使代码更简洁，而且由于其“零成本抽象”的特性，通常能编译出与手写循环性能相当的机器码。