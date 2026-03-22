# 015：Unsafe与内存安全 🛡️

![](img/c899e11dafb20a212ff9d2ea1c721164_1.png)

在本节课中，我们将要学习Rust中的`unsafe`代码以及内存安全的概念。我们将探讨为什么需要`unsafe`，它能做什么，以及如何安全地使用它来构建底层抽象。

![](img/c899e11dafb20a212ff9d2ea1c721164_3.png)

## 概述

到目前为止，我们在课程中使用的所有Rust代码都属于“安全Rust”（Safe Rust）的范畴。这意味着我们从未使用过`unsafe`这个关键字。安全Rust是一种内存安全的语言，它通过编译器的严格检查，帮助我们避免了诸如读取未初始化数据、悬垂指针、段错误、双重释放、释放后使用以及缓冲区溢出等严重的内存问题。

然而，有时我们需要进行系统级编程，需要更底层的控制，例如直接操作内存地址和指针。这时，我们就需要进入“不安全Rust”（Unsafe Rust）的领域。本节课我们将探讨安全与不安全Rust之间的关系，以及如何在不破坏Rust安全保证的前提下，使用`unsafe`来构建强大的底层抽象。

## 内存安全的重要性

内存安全意味着程序不会出现上述那些危险的内存错误。大多数现代高级语言（如Python、Java、JavaScript）在默认情况下都是内存安全的，或者通过运行时（如垃圾回收器）来管理内存安全。

像C和C++这样的低级语言本身并不保证内存安全。一个**正确编写**的C/C++程序可以是内存安全的，但语言本身将确保正确的责任交给了程序员。如果程序员犯错，编译器可能无法识别，从而导致程序编译通过但运行时出现未定义行为（Undefined Behavior）或内存安全问题。

我们可以用一个简单的图示来理解不同语言在“正确性”和“可编译性”上的权衡：

![](img/c899e11dafb20a212ff9d2ea1c721164_5.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_7.png)

*   **理想情况**：所有正确的程序都能编译，所有不正确的程序都不能编译。
*   **Rust的取舍**：Rust编译器非常严格，它会拒绝大量它认为可能不安全的程序（包括一些实际上正确的程序），以确保所有能编译的程序都是内存安全的。
*   **C/C++的取舍**：C/C++编译器相对宽松，会编译更多的程序（包括一些实际上不正确的程序），将验证正确性的责任留给了程序员。

![](img/c899e11dafb20a212ff9d2ea1c721164_9.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_11.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_12.png)

对于大多数应用开发，安全Rust的严格性是优点。但对于系统编程（如编写操作系统内核、嵌入式设备驱动、高性能数据结构），有时需要绕过编译器的安全检查来直接操作内存，这就是`unsafe`存在的意义。

## 引入Unsafe Rust

![](img/c899e11dafb20a212ff9d2ea1c721164_14.png)

Rust通过`unsafe`关键字来提供底层操作能力。关键理念是：**不安全Rust是安全Rust的超集**。任何有效的安全Rust代码在`unsafe`块中同样有效，但`unsafe`允许你执行一些额外的、编译器无法自动验证安全性的操作。

![](img/c899e11dafb20a212ff9d2ea1c721164_16.png)

`unsafe`的主要目标是：**用不安全的实现来构建安全的抽象**。例如，标准库中的`Vec<T>`、`String`等类型，其内部实现使用了`unsafe`代码来高效地管理内存，但它们对外暴露的API是完全安全的，用户无法通过安全代码导致内存错误。

## Unsafe允许的操作

![](img/c899e11dafb20a212ff9d2ea1c721164_18.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_20.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_22.png)

`unsafe`关键字只允许你进行以下五种操作，它并不会“关闭借用检查器”：

![](img/c899e11dafb20a212ff9d2ea1c721164_24.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_25.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_27.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_29.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_31.png)

1.  **解引用裸指针** (`*const T`, `*mut T`)
2.  **调用不安全函数**
3.  **访问或修改可变静态变量**
4.  **实现不安全trait**
5.  **访问联合体（Union）的字段**

![](img/c899e11dafb20a212ff9d2ea1c721164_33.png)

其中，**解引用裸指针**是最核心的能力，它让你能直接读写内存地址。创建裸指针是安全的，但使用（解引用）它们必须在`unsafe`块中。

## 安全抽象与不安全实现

![](img/c899e11dafb20a212ff9d2ea1c721164_35.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_37.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_39.png)

这是使用`unsafe`的核心模式。一个函数或模块可以对外提供安全的API，但在其内部使用`unsafe`代码来实现功能。开发者必须确保，无论用户如何使用这个安全API，都不会触发未定义行为。

![](img/c899e11dafb20a212ff9d2ea1c721164_41.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_43.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_44.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_46.png)

例如，`String::from_utf8_unchecked`函数就是一个不安全函数。它接受一个字节切片，并假设它已经是有效的UTF-8编码，然后直接将其转换为`String`。如果传入无效字节，将破坏`String`类型的内存安全不变性，导致未定义行为。因此，这个函数被标记为`unsafe`，调用者必须在`unsafe`块中调用它，并**自己负责**确保传入的字节是有效的。

![](img/c899e11dafb20a212ff9d2ea1c721164_48.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_50.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_52.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_54.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_56.png)

```rust
// 安全代码中无法调用
// let s = String::from_utf8_unchecked(invalid_bytes);

![](img/c899e11dafb20a212ff9d2ea1c721164_58.png)

unsafe {
    // 调用者必须确保 bytes 是有效的 UTF-8
    let s = String::from_utf8_unchecked(valid_bytes);
}
```

![](img/c899e11dafb20a212ff9d2ea1c721164_60.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_62.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_64.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_66.png)

与之对应的`safe`版本是`String::from_utf8`，它会检查字节有效性并返回`Result`，更安全但略有开销。

## 未定义行为与责任

![](img/c899e11dafb20a212ff9d2ea1c721164_68.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_70.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_72.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_74.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_75.png)

Rust同样有“未定义行为”的概念。如果代码触发了未定义行为（例如，解引用空指针、数据竞争），那么编译器可以假设你的程序永远不会做这些事，并基于此进行激进的优化，这可能导致任何不可预测的结果。

![](img/c899e11dafb20a212ff9d2ea1c721164_77.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_79.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_80.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_82.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_84.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_86.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_88.png)

在安全Rust中，编译器会确保你不会意外触发未定义行为。但在`unsafe`块中，**避免未定义行为的责任转移到了程序员身上**。编写`unsafe`代码时，你必须像C/C++程序员一样仔细推理，确保代码在所有情况下都是正确的。

![](img/c899e11dafb20a212ff9d2ea1c721164_90.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_92.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_94.png)

一段`unsafe`代码如果不可能被外部的安全代码以任何方式导致未定义行为，则被称为“健全的”（Sound）。反之，则是“不健全的”（Unsound），这是严重的错误。

![](img/c899e11dafb20a212ff9d2ea1c721164_96.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_97.png)

## 如何检查Unsafe代码的正确性

![](img/c899e11dafb20a212ff9d2ea1c721164_99.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_101.png)

编写正确的`unsafe`代码非常困难。以下是Rust生态中用于辅助验证的重要工具：

![](img/c899e11dafb20a212ff9d2ea1c721164_103.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_105.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_107.png)

*   **Miri**：一个Rust解释器，可以在执行时检测多种未定义行为（如越界访问、使用未初始化内存）。它运行缓慢，但非常适合在测试和CI中使用。
    ```bash
    cargo +nightly miri run
    cargo +nightly miri test
    ```

![](img/c899e11dafb20a212ff9d2ea1c721164_109.png)

*   **Sanitizers**：一系列运行时检测工具，可以集成到编译过程中。
    *   **AddressSanitizer (ASan)**：检测内存错误（如缓冲区溢出、释放后使用）。
    *   **MemorySanitizer (MSan)**：检测未初始化内存读取。
    *   **ThreadSanitizer (TSan)**：检测数据竞争。
    使用它们通常需要通过`-Z sanitizer`标志并在nightly工具链下编译。

![](img/c899e11dafb20a212ff9d2ea1c721164_111.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_112.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_114.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_116.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_118.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_119.png)

*   **Loom**：一个用于测试并发代码的库。它可以系统地遍历线程操作的所有可能交错顺序，帮助发现隐藏的数据竞争和死锁。
    ```rust
    #[test]
    fn test_concurrent_thing() {
        loom::model(|| {
            // 你的并发代码
        });
    }
    ```

![](img/c899e11dafb20a212ff9d2ea1c721164_121.png)

## 总结

![](img/c899e11dafb20a212ff9d2ea1c721164_123.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_125.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_127.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_128.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_130.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_132.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_134.png)

本节课我们一起学习了Rust中`unsafe`与内存安全的核心概念。

![](img/c899e11dafb20a212ff9d2ea1c721164_136.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_137.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_139.png)

*   我们回顾了内存安全的重要性以及Rust通过编译器严格检查来保障它的设计哲学。
*   我们理解了在某些系统编程场景下，需要绕过这些检查来获得底层控制能力，因此Rust引入了`unsafe`关键字。
*   我们明确了`unsafe`只允许进行五种特定操作，其核心思想是**用不安全的实现构建安全的抽象**。
*   我们认识到编写`unsafe`代码将避免未定义行为的责任交给了程序员，必须极其谨慎。
*   最后，我们介绍了几种强大的工具（Miri, Sanitizers, Loom）来帮助验证`unsafe`代码的正确性。

![](img/c899e11dafb20a212ff9d2ea1c721164_141.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_143.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_145.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_147.png)

![](img/c899e11dafb20a212ff9d2ea1c721164_148.png)

`unsafe`是Rust强大能力的基石，它使得用Rust自身实现标准库成为可能，但也是一把需要小心使用的双刃剑。在下一节课中，我们将尝试动手实践，使用`unsafe`来构建一个简单的`Vec`类型。