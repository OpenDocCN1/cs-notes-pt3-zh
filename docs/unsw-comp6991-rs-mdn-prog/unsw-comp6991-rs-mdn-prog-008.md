# 008：模块与测试 📦🧪


## 概述
在本节课中，我们将要学习Rust中关于代码组织和验证的两个核心概念：**模块系统**和**测试**。我们将了解如何将代码拆分为多个文件和模块，如何控制代码的可见性，以及如何为代码编写单元测试和文档测试，以确保其正确性。


---

![](img/66df70033965bd765c9c38ca16eddf09_5.png)

![](img/66df70033965bd765c9c38ca16eddf09_6.png)

## 模块化与可见性

![](img/66df70033965bd765c9c38ca16eddf09_8.png)

![](img/66df70033965bd765c9c38ca16eddf09_10.png)

上一节我们介绍了Rust的基本语法和所有权概念，本节中我们来看看如何组织和管理大型项目。

Rust的模块系统允许你将代码分割到不同的文件和目录中，这有助于管理大型项目。一个`cargo`项目（`package`）可以包含多个`crate`（可编译单元）。最常见的两种`crate`是：
*   **二进制crate (`src/main.rs`)**：生成可执行文件。
*   **库crate (`src/lib.rs`)**：生成供其他crate使用的代码库。

将核心逻辑放在库crate中，让二进制crate只负责调用，是一种非常常见且地道的做法，它提高了代码的复用性。

![](img/66df70033965bd765c9c38ca16eddf09_12.png)

![](img/66df70033965bd765c9c38ca16eddf09_13.png)

### 定义与使用模块
模块是代码组织的核心单元。你可以使用`mod`关键字来定义一个模块。

![](img/66df70033965bd765c9c38ca16eddf09_15.png)

**内联模块**：直接在文件中用花括号定义。
```rust
pub mod inline_module {
    pub fn foo() {
        println!("Food");
    }
}
```

**文件模块**：通过`mod module_name;`声明，Rust会在同级目录下寻找`module_name.rs`文件作为模块内容。

**目录模块**：通过`mod folder_name;`声明，Rust会在`folder_name/`目录下寻找`mod.rs`文件作为模块入口。

要从其他模块或crate中访问模块内的项（函数、结构体等），需要使用`use`关键字将其引入作用域，或者使用完整路径。

```rust
// 使用完整路径
let result = my_crate::inline_module::foo();

// 使用use引入作用域
use my_crate::inline_module::foo;
let result = foo();
```

### 可见性修饰符
Rust中所有项默认是**私有的**。使用`pub`关键字可以控制其可见范围。

以下是主要的可见性修饰符：
*   `pub`: 完全公开，可以从任何地方访问。
*   `pub(crate)`: 仅在当前crate内可见。
*   `pub(in path)`: 仅在指定路径的模块内可见（例如 `pub(in my_crate::some_module)`）。
*   `pub(super)`: 仅在父模块中可见。
*   （无修饰符）或 `pub(self)`: 仅在当前模块内可见（私有）。

### 使用 `pub use` 进行重导出
`pub use` 允许你将一个模块内部的项引入当前模块的作用域，并**同时将其公开**。这常用于创建一个清晰的公共API，隐藏内部复杂的模块结构。

![](img/66df70033965bd765c9c38ca16eddf09_17.png)

![](img/66df70033965bd765c9c38ca16eddf09_19.png)


```rust
// 在 src/lib.rs 中
pub mod complex {
    pub mod internal {
        pub fn useful_function() {}
    }
}
// 重导出，用户可以直接使用 `my_crate::useful_function`
pub use complex::internal::useful_function;
```

---

## 单元测试

![](img/66df70033965bd765c9c38ca16eddf09_23.png)

![](img/66df70033965bd765c9c38ca16eddf09_24.png)

上一节我们学习了如何组织代码，本节中我们来看看如何确保这些代码的正确性。

![](img/66df70033965bd765c9c38ca16eddf09_26.png)

![](img/66df70033965bd765c9c38ca16eddf09_28.png)

![](img/66df70033965bd765c9c38ca16eddf09_30.png)

Rust对测试提供了原生支持。单元测试通常与它们要测试的代码放在同一个文件中。

![](img/66df70033965bd765c9c38ca16eddf09_32.png)

![](img/66df70033965bd765c9c38ca16eddf09_34.png)

![](img/66df70033965bd765c9c38ca16eddf09_35.png)

### 编写测试
使用 `#[test]` 属性标记一个函数，它就会成为一个测试函数。在测试函数内部，使用 `assert!`、`assert_eq!`、`assert_ne!` 等宏来验证代码行为。

```rust
pub fn add_two(a: i32, b: i32) -> i32 {
    a + b
}

#[test]
fn test_add_two() {
    assert_eq!(add_two(2, 3), 5);
    assert_eq!(add_two(5, 10), 15);
}
```

### 运行测试
使用 `cargo test` 命令运行所有测试。你可以通过参数来过滤测试：
*   `cargo test test_add_two`：运行单个测试。
*   `cargo test --lib`：只运行库crate的单元测试。

### 测试组织与 `should_panic`
通常，我们会将测试集中在一个专门的模块中，并使用 `#[cfg(test)]` 属性来确保测试代码只在运行测试时被编译。

![](img/66df70033965bd765c9c38ca16eddf09_37.png)

```rust
#[cfg(test)]
mod tests {
    use super::*; // 引入外部模块的所有项

    #[test]
    fn it_works() {
        assert_eq!(add_two(2, 2), 4);
    }

    #[test]
    #[should_panic] // 这个测试应该触发panic
    fn this_panics() {
        panic!("This test is supposed to fail!");
    }
}
```

![](img/66df70033965bd765c9c38ca16eddf09_39.png)

![](img/66df70033965bd765c9c38ca16eddf09_41.png)

![](img/66df70033965bd765c9c38ca16eddf09_43.png)

### 集成测试
集成测试位于项目根目录的 `tests/` 文件夹中，它们将你的库作为一个外部crate来测试，主要用于测试公共API。每个文件都是一个独立的crate。



---

![](img/66df70033965bd765c9c38ca16eddf09_49.png)

![](img/66df70033965bd765c9c38ca16eddf09_51.png)

![](img/66df70033965bd765c9c38ca16eddf09_52.png)

![](img/66df70033965bd765c9c38ca16eddf09_54.png)

## 文档与文档测试 📝

上一节我们介绍了验证代码逻辑的单元测试，本节中我们来看看另一种特殊的测试——文档测试，它同时保证了文档示例的正确性。






Rust的文档注释使用三斜杠 `///`，支持Markdown格式。`cargo doc` 命令可以生成美观的HTML文档。





![](img/66df70033965bd765c9c38ca16eddf09_72.png)


### 编写文档注释
```rust
/// 将两个数字相加。
///
/// # 示例
/// ```
/// use my_crate::add_two;
/// let sum = add_two(2, 3);
/// assert_eq!(sum, 5);
/// ```
pub fn add_two(a: i32, b: i32) -> i32 {
    a + b
}
```



![](img/66df70033965bd765c9c38ca16eddf09_80.png)




### 文档测试
在文档注释的代码块中编写的示例，会被Rust自动识别为**文档测试**。当你运行 `cargo test` 时，这些示例也会被编译和执行，确保你的文档永远与代码同步。


![](img/66df70033965bd765c9c38ca16eddf09_90.png)

![](img/66df70033965bd765c9c38ca16eddf09_92.png)

![](img/66df70033965bd765c9c38ca16eddf09_94.png)

![](img/66df70033965bd765c9c38ca16eddf09_95.png)





你可以使用 `#` 开头的行在文档中隐藏一些辅助代码，这些代码在文档中不可见，但测试时会包含。



![](img/66df70033965bd765c9c38ca16eddf09_107.png)

![](img/66df70033965bd765c9c38ca16eddf09_109.png)

![](img/66df70033965bd765c9c38ca16eddf09_111.png)

![](img/66df70033965bd765c9c38ca16eddf09_113.png)

```rust
/// ```
/// # // 这行在生成的文档中会被隐藏
/// # use my_crate::setup_complex_system;
/// # let x = setup_complex_system();
/// let result = x.do_something();
/// assert!(result.is_ok());
/// ```
```

![](img/66df70033965bd765c9c38ca16eddf09_115.png)

### 链接到其他项
在文档中，你可以使用 `[`...`]` 语法链接到其他类型或函数，Rustdoc会自动生成链接。

```rust
/// 这个函数和 [`Foo`] 类型一起使用效果更好。
/// 更多细节参见 [`crate::module::some_function`]。
```

![](img/66df70033965bd765c9c38ca16eddf09_117.png)

![](img/66df70033965bd765c9c38ca16eddf09_119.png)

![](img/66df70033965bd765c9c38ca16eddf09_121.png)

### 强制文档
你可以在 `lib.rs` 顶部添加属性 `#![warn(missing_docs)]` 或 `#![deny(missing_docs)]`，让编译器对未文档化的公共项发出警告或直接报错，这有助于保持文档的完整性。

![](img/66df70033965bd765c9c38ca16eddf09_123.png)

![](img/66df70033965bd765c9c38ca16eddf09_125.png)

---

![](img/66df70033965bd765c9c38ca16eddf09_127.png)

![](img/66df70033965bd765c9c38ca16eddf09_129.png)

## 总结
本节课中我们一起学习了Rust项目组织的核心机制。
1.  **模块系统**：我们了解了如何使用 `mod`、`use` 和 `pub` 来拆分代码、管理作用域和构建清晰的API。
2.  **单元测试**：我们掌握了如何使用 `#[test]` 编写测试，以及如何用 `cargo test` 运行它们，这是保证代码质量的基础。
3.  **文档与文档测试**：我们学习了如何编写 `///` 文档注释，并利用其内置的文档测试功能，确保示例代码永远正确，这极大地提升了库的可用性和可靠性。

![](img/66df70033965bd765c9c38ca16eddf09_131.png)

![](img/66df70033965bd765c9c38ca16eddf09_133.png)

![](img/66df70033965bd765c9c38ca16eddf09_134.png)

将这些概念应用到你的项目中，尤其是第一个作业中，将帮助你构建出结构清晰、易于维护且值得信赖的Rust代码。