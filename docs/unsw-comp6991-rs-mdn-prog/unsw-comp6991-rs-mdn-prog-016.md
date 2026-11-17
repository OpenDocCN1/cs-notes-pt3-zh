# 016：Unsafe封装与FFI

![](img/f64999e9bb3be52c75cf9a34aa5850b1_1.png)

![](img/f64999e9bb3be52c75cf9a34aa5850b1_3.png)

![](img/f64999e9bb3be52c75cf9a34aa5850b1_5.png)

![](img/f64999e9bb3be52c75cf9a34aa5850b1_7.png)

## 概述

![](img/f64999e9bb3be52c75cf9a34aa5850b1_9.png)

![](img/f64999e9bb3be52c75cf9a34aa5850b1_11.png)

![](img/f64999e9bb3be52c75cf9a34aa5850b1_12.png)

在本节课中，我们将学习Rust中两个高级且强大的主题：如何安全地封装`unsafe`代码来构建抽象，以及如何使用外部函数接口（FFI）来调用其他语言（如C）编写的库。我们将通过动手实践来理解这些概念，包括尝试构建一个简易的`Vec`类型，以及从Rust中调用C语言编写的`libcurl`库来获取网页内容。

![](img/f64999e9bb3be52c75cf9a34aa5850b1_14.png)

![](img/f64999e9bb3be52c75cf9a34aa5850b1_16.png)

## 构建简易的 `MyVec<T>`

上一节我们介绍了`unsafe`代码块和原始指针的基本概念。本节中，我们来看看如何利用这些知识，尝试构建一个我们自己的、简易版本的动态数组 `MyVec<T>`。我们的目标是理解标准库中`Vec`背后的核心思想，并亲身体验封装`unsafe`操作时需要注意的种种细节。

### 定义 `MyVec` 结构

首先，我们需要定义`MyVec`的数据结构。一个动态数组需要管理一块在堆上分配的内存，并跟踪其当前元素数量以及总容量。

```rust
struct MyVec<T> {
    pointer: *mut T,      // 指向堆上分配内存的原始指针
    size: usize,          // 当前存储的元素数量
    capacity: usize,      // 当前分配的内存可以容纳的元素数量
}
```

这里，`pointer` 是一个 `*mut T` 类型的原始指针，它指向我们为 `T` 类型元素分配的内存块。`size` 和 `capacity` 分别记录已用空间和总空间。

### 实现 `new` 方法

初始时，向量为空，没有分配任何内存。我们将指针设为空指针，并将大小和容量都设为0。

```rust
impl<T> MyVec<T> {
    pub fn new() -> Self {
        MyVec {
            pointer: std::ptr::null_mut(),
            size: 0,
            capacity: 0,
        }
    }
}
```

### 实现 `push` 方法

`push` 方法用于向向量末尾添加一个元素。在添加之前，我们需要确保有足够的空间。

以下是实现 `push` 方法的关键步骤：

1.  **检查容量**：如果当前元素数量 `size` 等于容量 `capacity`，说明空间已满，需要扩容。
2.  **扩容**：我们通过一个辅助函数 `expand_capacity` 来分配更多内存。
3.  **计算写入位置**：使用 `pointer_to_elem` 辅助函数，根据当前 `size` 计算出新元素应该存放的内存地址。
4.  **写入数据**：使用 `std::ptr::write` 将值写入计算出的地址。**必须使用 `write` 而不是直接赋值（`*ptr = value`）**，因为直接赋值会尝试读取旧值并调用其析构器，而新分配的内存是未初始化的，这会导致未定义行为。
5.  **更新大小**：成功写入后，将 `size` 加1。

```rust
pub fn push(&mut self, value: T) {
    if self.size == self.capacity {
        self.expand_capacity();
    }
    unsafe {
        let ptr = self.pointer_to_elem(self.size);
        std::ptr::write(ptr, value);
        self.size += 1;
    }
}

// 辅助函数：获取指向第 index 个元素的指针
unsafe fn pointer_to_elem(&self, index: usize) -> *mut T {
    // 安全条件：index 必须小于等于当前容量
    self.pointer.add(index)
}

// 辅助函数：扩容
fn expand_capacity(&mut self) {
    let new_capacity = if self.capacity == 0 {
        4 // 初始容量
    } else {
        self.capacity.checked_mul(2).expect("Capacity overflow")
    };

    let new_layout = std::alloc::Layout::array::<T>(new_capacity).unwrap();

    let new_ptr = if self.capacity == 0 {
        unsafe { std::alloc::alloc(new_layout) as *mut T }
    } else {
        let old_layout = std::alloc::Layout::array::<T>(self.capacity).unwrap();
        let old_ptr = self.pointer as *mut u8;
        unsafe { std::alloc::realloc(old_ptr, old_layout, new_layout.size()) as *mut T }
    };

    self.pointer = new_ptr;
    self.capacity = new_capacity;
}
```

### 实现 `pop` 方法

`pop` 方法移除并返回最后一个元素。如果向量为空，则返回 `None`。

1.  **检查是否为空**：如果 `size` 为0，返回 `None`。
2.  **减小大小**：将 `size` 减1，获取移除前最后一个元素的索引。
3.  **读取数据**：使用 `std::ptr::read` 从该地址读取值。这会获取元素的所有权，但不会调用源地址的析构器（因为元素已被移出）。
4.  **返回值**：将读取的值包装在 `Some` 中返回。

```rust
pub fn pop(&mut self) -> Option<T> {
    if self.size == 0 {
        return None;
    }
    self.size -= 1;
    let index = self.size;
    unsafe {
        let ptr = self.pointer_to_elem(index);
        Some(std::ptr::read(ptr))
    }
}
```

### 实现 `get` 方法

`get` 方法返回一个到索引处元素的不可变引用。如果索引越界，则返回 `None`。

**关键点**：`get` 应该返回一个引用（`&T`），而不是值（`T`）。因为调用者可能只是查看数据，而不想取得其所有权。多次调用 `get` 获得同一元素的多个副本在语义上是错误的，并且如果 `T` 没有实现 `Copy`，会导致问题。

![](img/f64999e9bb3be52c75cf9a34aa5850b1_18.png)

![](img/f64999e9bb3be52c75cf9a34aa5850b1_19.png)

1.  **检查索引**：如果 `index >= size`，返回 `None`。
2.  **获取指针并解引用**：在 `unsafe` 块中获取指针，然后通过 `&*ptr` 将其转换为引用。这个引用的生命周期与传入的 `&self` 相关联。

```rust
pub fn get(&self, index: usize) -> Option<&T> {
    if index >= self.size {
        return None;
    }
    unsafe {
        let ptr = self.pointer_to_elem(index);
        Some(&*ptr)
    }
}
```

### 实现 `Drop` trait

当 `MyVec` 离开作用域时，我们需要释放其占用的堆内存，并确保所有存储的元素都被正确析构。

1.  **析构元素**：遍历所有有效元素（0 到 `size`），使用 `std::ptr::drop_in_place` 显式调用每个元素的析构器。
2.  **释放内存**：使用 `std::alloc::dealloc` 释放整个内存块。

![](img/f64999e9bb3be52c75cf9a34aa5850b1_21.png)

![](img/f64999e9bb3be52c75cf9a34aa5850b1_22.png)

```rust
impl<T> Drop for MyVec<T> {
    fn drop(&mut self) {
        if !self.pointer.is_null() {
            // 首先析构所有剩余元素
            for i in 0..self.size {
                unsafe {
                    std::ptr::drop_in_place(self.pointer_to_elem(i));
                }
            }
            // 然后释放内存
            let layout = std::alloc::Layout::array::<T>(self.capacity).unwrap();
            unsafe {
                std::alloc::dealloc(self.pointer as *mut u8, layout);
            }
        }
    }
}
```

### 封装 Unsafe 抽象

我们构建的 `MyVec` 内部包含 `unsafe` 代码，但它为外部提供了一个安全的接口（`push`, `pop`, `get` 都是安全的 `pub` 函数）。然而，为了维持内部不变式（invariant），我们必须将结构体的字段标记为私有（`private`）。如果 `pointer`、`size` 和 `capacity` 是公有的，那么安全代码就可以随意修改它们，从而破坏我们 `unsafe` 代码所依赖的前提条件，导致未定义行为。

因此，最佳实践是将包含 `unsafe` 实现的模块或结构体的内部状态完全隐藏起来。

```rust
pub mod myvec {
    struct MyVec<T> { /* 私有字段 */ }
    impl<T> MyVec<T> {
        pub fn new() -> Self { ... }
        pub fn push(&mut self, value: T) { ... }
        // 其他公共安全接口
    }
}
```

![](img/f64999e9bb3be52c75cf9a34aa5850b1_24.png)

## 外部函数接口（FFI）

上一节我们探讨了在Rust内部封装不安全操作。本节中，我们来看看如何跨越语言边界，使用外部函数接口（FFI）来调用其他语言编写的代码，这里以C语言为例。

![](img/f64999e9bb3be52c75cf9a34aa5850b1_26.png)

![](img/f64999e9bb3be52c75cf9a34aa5850b1_27.png)

![](img/f64999e9bb3be52c75cf9a34aa5850b1_29.png)

FFI 允许 Rust 程序与 C 库在同一进程中交互，这非常强大但也非常危险，因为Rust的安全保证在跨越FFI边界后不再有效。

![](img/f64999e9bb3be52c75cf9a34aa5850b1_31.png)

![](img/f64999e9bb3be52c75cf9a34aa5850b1_33.png)

![](img/f64999e9bb3be52c75cf9a34aa5850b1_35.png)

### 手动绑定到 C 库：以 libcurl 为例

![](img/f64999e9bb3be52c75cf9a34aa5850b1_37.png)

我们将尝试从Rust调用著名的C网络库 `libcurl` 来获取一个网页。

![](img/f64999e9bb3be52c75cf9a34aa5850b1_39.png)

首先，需要在Rust中声明C库提供的函数和类型。这通过 `extern` 块完成。


![](img/f64999e9bb3be52c75cf9a34aa5850b1_41.png)

![](img/f64999e9bb3be52c75cf9a34aa5850b1_43.png)

![](img/f64999e9bb3be52c75cf9a34aa5850b1_45.png)

![](img/f64999e9bb3be52c75cf9a34aa5850b1_47.png)


![](img/f64999e9bb3be52c75cf9a34aa5850b1_49.png)

```rust
use std::ffi::CString;
use std::os::raw::{c_void, c_long, c_char};
// 定义C库中使用的类型
type CURL = c_void;
enum CURLoption {
    CURLOPT_URL = 10002, // 来自 curl.h 的实际值
}
enum CURLcode {
    CURLE_OK = 0,
    // ... 其他代码
}
// 声明外部C函数
#[link(name = "curl")]
extern "C" {
    fn curl_easy_init() -> *mut CURL;
    fn curl_easy_setopt(curl: *mut CURL, option: CURLoption, parameter: *const c_char) -> CURLcode;
    fn curl_easy_perform(curl: *mut CURL) -> CURLcode;
    fn curl_easy_cleanup(curl: *mut CURL);
}
```

![](img/f64999e9bb3be52c75cf9a34aa5850b1_51.png)

`#[link(name = "curl")]` 属性告诉Rust链接器去寻找名为 `libcurl` 的库。

![](img/f64999e9bb3be52c75cf9a34aa5850b1_53.png)

接下来，我们可以在一个 `unsafe` 块中调用这些函数：

```rust
fn fetch_url(url: &str) -> Result<(), CURLcode> {
    unsafe {
        let curl = curl_easy_init();
        if curl.is_null() {
            return Err(/* 错误处理 */);
        }

        let c_url = CString::new(url).unwrap();
        let url_param = c_url.as_ptr() as *const c_char;

        let setopt_result = curl_easy_setopt(curl, CURLoption::CURLOPT_URL, url_param);
        if setopt_result != CURLcode::CURLE_OK {
            curl_easy_cleanup(curl);
            return Err(setopt_result);
        }

        let perform_result = curl_easy_perform(curl);
        curl_easy_cleanup(curl);

        if perform_result == CURLcode::CURLE_OK {
            Ok(())
        } else {
            Err(perform_result)
        }
    }
}
```

![](img/f64999e9bb3be52c75cf9a34aa5850b1_55.png)

![](img/f64999e9bb3be52c75cf9a34aa5850b1_57.png)

![](img/f64999e9bb3be52c75cf9a34aa5850b1_59.png)

### 使用工具简化 FFI

![](img/f64999e9bb3be52c75cf9a34aa5850b1_61.png)

![](img/f64999e9bb3be52c75cf9a34aa5850b1_63.png)

![](img/f64999e9bb3be52c75cf9a34aa5850b1_64.png)

![](img/f64999e9bb3be52c75cf9a34aa5850b1_65.png)

手动编写FFI绑定既繁琐又容易出错。幸运的是，有强大的工具可以自动化这个过程：

![](img/f64999e9bb3be52c75cf9a34aa5850b1_67.png)

![](img/f64999e9bb3be52c75cf9a34aa5850b1_68.png)

![](img/f64999e9bb3be52c75cf9a34aa5850b1_70.png)

*   **bindgen**： 这是一个可以从C/C++头文件自动生成Rust FFI绑定代码的工具。你只需要提供头文件，它就会输出对应的 `extern` 块和类型定义。
*   **现成的绑定 Crate**： 对于大多数流行的C库，Rust社区通常已经提供了维护良好的绑定crate。例如，对于 `libcurl`，有 `curl-sys` crate 提供了底层绑定，而 `curl` crate 则在 `curl-sys` 之上提供了更符合Rust习惯的、安全的抽象API。

![](img/f64999e9bb3be52c75cf9a34aa5850b1_72.png)

![](img/f64999e9bb3be52c75cf9a34aa5850b1_73.png)

使用这些工具或crate可以极大地提高开发效率并减少错误。

![](img/f64999e9bb3be52c75cf9a34aa5850b1_75.png)

![](img/f64999e9bb3be52c75cf9a34aa5850b1_77.png)

## 总结

![](img/f64999e9bb3be52c75cf9a34aa5850b1_79.png)

![](img/f64999e9bb3be52c75cf9a34aa5850b1_80.png)

本节课中我们一起学习了Rust中两个关键的高级主题。

![](img/f64999e9bb3be52c75cf9a34aa5850b1_82.png)

首先，我们深入探讨了如何通过封装 `unsafe` 代码块来构建安全的抽象。我们以构建简易的 `MyVec<T>` 为例，实践了内存分配、扩容、数据读写、析构以及内存释放的全过程。我们特别强调了维持内部不变式的重要性（通过私有字段），以及在使用原始指针时必须注意的细微之处，例如使用 `ptr::write` 避免读取未初始化内存，以及正确地区分返回引用（`get`）和所有权（`pop`）。

![](img/f64999e9bb3be52c75cf9a34aa5850b1_84.png)

![](img/f64999e9bb3be52c75cf9a34aa5850b1_86.png)

其次，我们介绍了外部函数接口（FFI）。我们看到了如何通过 `extern` 块声明C函数和类型，并在 `unsafe` 块中调用它们，从而实现Rust与C库的交互。我们也了解了使用 `bindgen` 等自动化工具或社区维护的绑定crate可以极大地简化这一过程。

![](img/f64999e9bb3be52c75cf9a34aa5850b1_88.png)

![](img/f64999e9bb3be52c75cf9a34aa5850b1_89.png)

通过结合 `unsafe` 封装和 FFI，Rust 能够在不牺牲安全性的核心承诺的前提下，实现极致的性能控制并与庞大的现有C/C++生态系统无缝集成。