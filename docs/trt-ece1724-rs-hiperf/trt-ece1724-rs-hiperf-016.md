# 016：智能指针 part2

![](img/f0ff31812e93ed4785df1d52bdc08a0f_0.png)

在本节课中，我们将要学习智能指针的更多高级概念，包括宽指针、`Deref`和`Drop`特质的实现，以及`Rc`和`RefCell`这两种特殊的智能指针。这些知识将帮助你理解Rust如何管理内存和实现多态。

![](img/f0ff31812e93ed4785df1d52bdc08a0f_2.png)

![](img/f0ff31812e93ed4785df1d52bdc08a0f_3.png)

## 宽指针与动态大小类型

![](img/f0ff31812e93ed4785df1d52bdc08a0f_5.png)

![](img/f0ff31812e93ed4785df1d52bdc08a0f_6.png)

![](img/f0ff31812e93ed4785df1d52bdc08a0f_7.png)

上一节我们介绍了动态大小类型。本节中我们来看看宽指针。

宽指针，有时也称为胖指针，是一种带有元数据的智能指针。它们是将动态大小类型转换为已知大小类型的常用方法。例如，`&str`是一个字符串切片，属于动态大小类型，因为我们不知道其具体长度。为了使其具有已知大小，我们使用`&str`，这实际上是一个宽指针。

![](img/f0ff31812e93ed4785df1d52bdc08a0f_9.png)

![](img/f0ff31812e93ed4785df1d52bdc08a0f_11.png)

一个指向切片的宽指针包含两个部分：数据的地址和切片的长度。这使得编译器能够将其视为实现了`Sized`特质的类型。

以下是宽指针的典型结构：
```rust
// 宽指针结构示意（非实际代码）
struct WidePointer {
    data_address: *const u8,
    length: usize,
}
```

![](img/f0ff31812e93ed4785df1d52bdc08a0f_13.png)

![](img/f0ff31812e93ed4785df1d52bdc08a0f_14.png)

## 特质对象的宽指针

![](img/f0ff31812e93ed4785df1d52bdc08a0f_16.png)

现在，让我们讨论指向特质对象的宽指针。

一个指向特质对象（如`dyn Animal`）的宽指针由两部分组成：一个数据指针和一个虚函数表指针。

![](img/f0ff31812e93ed4785df1d52bdc08a0f_18.png)

![](img/f0ff31812e93ed4785df1d52bdc08a0f_19.png)

![](img/f0ff31812e93ed4785df1d52bdc08a0f_21.png)

*   **数据指针**：指向存储特质对象具体数据的内存地址。
*   **虚函数表指针**：指向一个虚函数表，该表是一个包含多个函数指针的结构体，每个指针指向特质中每个方法的具体实现代码。

由于特质对象的动态特性，我们无法在编译时知道应该调用哪个具体的方法实现。因此，需要在运行时通过查询虚函数表来决定。这种机制被称为**动态分发**。

![](img/f0ff31812e93ed4785df1d52bdc08a0f_23.png)

这与C++中实现多态（ polymorphism ）的机制类似。Rust通过特质对象和虚函数表同样可以实现多态，但方式更为受限：Rust的特质只能包含方法，不能包含数据字段。

![](img/f0ff31812e93ed4785df1d52bdc08a0f_25.png)

![](img/f0ff31812e93ed4785df1d52bdc08a0f_26.png)

使用这种动态分发会带来额外的开销，因为每次方法调用都需要一次虚函数表查找。这是为实现运行时多态性所付出的代价。

## 实现 `Deref` 特质

![](img/f0ff31812e93ed4785df1d52bdc08a0f_28.png)

![](img/f0ff31812e93ed4785df1d52bdc08a0f_30.png)

接下来，我们看看如何为自定义智能指针实现 `Deref` 和 `Drop` 特质。首先从 `Deref` 特质开始。

`Deref` 特质允许将智能指针当作普通引用来使用。当我们使用解引用运算符 `*` 时，实际上调用的是 `deref` 方法。

![](img/f0ff31812e93ed4785df1d52bdc08a0f_32.png)

![](img/f0ff31812e93ed4785df1d52bdc08a0f_33.png)

Rust标准库中的 `Box<T>` 已经实现了 `Deref`。例如：
```rust
let x = 5;
let y = Box::new(x); // 将x装箱
assert_eq!(5, *y); // 解引用y，调用 y.deref()
```

![](img/f0ff31812e93ed4785df1d52bdc08a0f_35.png)

现在，假设我们想为自己的类型实现 `Deref`。我们定义一个简单的元组结构体 `MyBox`。

```rust
struct MyBox<T>(T); // 一个元组结构体，包装类型T

impl<T> MyBox<T> {
    fn new(x: T) -> MyBox<T> {
        MyBox(x)
    }
}
```

此时，我们还不能对 `MyBox` 使用 `*` 运算符进行解引用，因为它尚未实现 `Deref` 特质。

以下是实现 `Deref` 特质的方法：
```rust
use std::ops::Deref;

impl<T> Deref for MyBox<T> {
    type Target = T; // 定义关联类型为T

    fn deref(&self) -> &Self::Target {
        &self.0 // 返回内部数据的引用
    }
}
```
实现后，当我们编写 `*y` （其中 `y` 是 `MyBox<T>`）时，Rust实际上会将其转换为 `*(y.deref())`。首先调用 `deref` 方法获取内部数据的引用，然后再对这个引用进行解引用。

![](img/f0ff31812e93ed4785df1d52bdc08a0f_37.png)

## 解引用强制多态

![](img/f0ff31812e93ed4785df1d52bdc08a0f_39.png)

Rust提供了称为“解引用强制多态”的语法糖，让代码更简洁。

![](img/f0ff31812e93ed4785df1d52bdc08a0f_41.png)

![](img/f0ff31812e93ed4785df1d52bdc08a0f_43.png)

![](img/f0ff31812e93ed4785df1d52bdc08a0f_45.png)

![](img/f0ff31812e93ed4785df1d52bdc08a0f_47.png)

考虑以下例子：
```rust
fn hello(name: &str) {
    println!("Hello, {}!", name);
}

let m = MyBox::new(String::from("Rust"));
hello(&m);
```
这里，`hello` 函数接收一个 `&str` 参数。我们传入的是 `&MyBox<String>`。Rust编译器会进行以下自动转换：
1.  `&m` 触发 `MyBox<String>` 的 `deref` 方法，得到 `&String`。
2.  Rust标准库为 `String` 实现了自动解引用到 `&str`，因此 `&String` 被强制转换为 `&str`。

![](img/f0ff31812e93ed4785df1d52bdc08a0f_49.png)

这一切都在编译时完成，无需我们手动转换，使得API调用更加友好。

![](img/f0ff31812e93ed4785df1d52bdc08a0f_51.png)

除了 `Deref`，还有 `DerefMut` 特质用于获取可变引用。其规则与 `Deref` 类似，但需要注意所有权规则：可以将可变引用转换为不可变引用（通过 `Deref`），但不能将不可变引用转换为可变引用，因为这可能违反引用安全规则。

![](img/f0ff31812e93ed4785df1d52bdc08a0f_53.png)

## 实现 `Drop` 特质

现在，让我们讨论 `Drop` 特质。

通过实现 `Drop` 特质中的 `drop` 方法，可以自定义当值离开作用域时发生的清理逻辑。这对于释放资源（如内存、文件句柄、网络连接）非常有用。

![](img/f0ff31812e93ed4785df1d52bdc08a0f_55.png)

为我们的 `MyBox` 实现一个简单的 `Drop`：
```rust
impl<T> Drop for MyBox<T> {
    fn drop(&mut self) {
        println!("Dropping MyBox!");
        // 这里可以添加释放资源的代码
    }
}
```
当 `MyBox` 的实例离开作用域时，会自动调用此 `drop` 方法并打印信息。

通常，我们无法手动调用 `drop` 方法（例如 `y.drop()`），因为这会导致在作用域结束时再次调用，引发“双重释放”错误。如果确实需要提前释放资源，应使用 `std::mem::drop` 函数：
```rust
let y = MyBox::new(5);
drop(y); // 显式提前丢弃y
// 此时y已失效，不能再使用
```

## `Rc<T>` 引用计数智能指针

![](img/f0ff31812e93ed4785df1d52bdc08a0f_57.png)

![](img/f0ff31812e93ed4785df1d52bdc08a0f_59.png)

![](img/f0ff31812e93ed4785df1d52bdc08a0f_60.png)

接下来，我们介绍两种特殊的智能指针。首先是 `Rc<T>`，即引用计数智能指针。

Rust的所有权规则通常要求一个数据只有一个所有者。`Rc<T>` 允许数据有多个所有者，它通过引用计数来追踪所有者的数量。只有当引用计数变为零时，数据才会被清理。

`Rc<T>` 只适用于单线程场景，并且它提供的是不可变引用，意味着数据是只读的。这在需要共享数据但不需要修改的场景中非常有用，例如图结构中的多个边指向同一个节点。

以下是 `Rc<T>` 的基本用法：
```rust
use std::rc::Rc;

![](img/f0ff31812e93ed4785df1d52bdc08a0f_62.png)

![](img/f0ff31812e93ed4785df1d52bdc08a0f_63.png)

let first = Rc::new(String::from("hello"));
println!("count after creating first = {}", Rc::strong_count(&first)); // 计数为1

![](img/f0ff31812e93ed4785df1d52bdc08a0f_65.png)

![](img/f0ff31812e93ed4785df1d52bdc08a0f_67.png)

{
    let second = Rc::clone(&first); // 克隆Rc，增加计数，不克隆底层数据
    println!("count after creating second = {}", Rc::strong_count(&first)); // 计数为2
    println!("first: {}, second: {}", *first, *second); // 解引用获取数据
} // second离开作用域，计数减1

println!("count after second goes out of scope = {}", Rc::strong_count(&first)); // 计数恢复为1
```
在多线程环境下，需要使用 `Arc<T>`（原子引用计数）来替代 `Rc<T>`。

![](img/f0ff31812e93ed4785df1d52bdc08a0f_69.png)

## `RefCell<T>` 与内部可变性模式

最后，我们看看 `RefCell<T>`。它实现了“内部可变性”设计模式。

![](img/f0ff31812e93ed4785df1d52bdc08a0f_71.png)

`RefCell<T>` 在运行时而非编译时执行借用检查规则。它允许你在拥有不可变引用的同时，修改其内部的数据。这在一定程度上绕过了编译时严格的借用检查，但将错误检查推迟到了运行时。如果运行时违反了借用规则（例如，同时存在多个可变借用），程序会 `panic`。

`RefCell<T>` 通常与 `Rc<T>` 结合使用，以在单线程场景下实现共享的可变状态。

以下是 `RefCell<T>` 与 `Rc<T>` 结合使用的示例：
```rust
use std::rc::Rc;
use std::cell::RefCell;

![](img/f0ff31812e93ed4785df1d52bdc08a0f_73.png)

let counter = Rc::new(RefCell::new(0)); // 用Rc包装RefCell

![](img/f0ff31812e93ed4785df1d52bdc08a0f_75.png)

let c1 = Rc::clone(&counter);
let c2 = Rc::clone(&counter);

![](img/f0ff31812e93ed4785df1d52bdc08a0f_76.png)

// 通过第一个引用修改值
{
    let mut num = c1.borrow_mut(); // 获取可变借用
    *num += 1;
} // num离开作用域，可变借用释放

![](img/f0ff31812e93ed4785df1d52bdc08a0f_78.png)

// 通过第二个引用修改值
{
    let mut num = c2.borrow_mut();
    *num += 2;
}

![](img/f0ff31812e93ed4785df1d52bdc08a0f_80.png)

![](img/f0ff31812e93ed4785df1d52bdc08a0f_82.png)

![](img/f0ff31812e93ed4785df1d52bdc08a0f_84.png)

![](img/f0ff31812e93ed4785df1d52bdc08a0f_86.png)

// 读取最终值
println!("Final counter value: {}", *counter.borrow()); // 输出: 3
```
`borrow_mut` 方法返回一个 `RefMut<T>` 智能指针，`borrow` 方法返回一个 `Ref<T>` 智能指针。它们分别代表可变借用和不可变借用，并在运行时管理借用规则。

![](img/f0ff31812e93ed4785df1d52bdc08a0f_88.png)

![](img/f0ff31812e93ed4785df1d52bdc08a0f_90.png)

![](img/f0ff31812e93ed4785df1d52bdc08a0f_91.png)

在多线程环境下，需要使用 `Mutex<T>`（互斥锁）来替代 `RefCell<T>`，通常与 `Arc<T>` 结合为 `Arc<Mutex<T>>`，以实现线程间安全的共享可变状态。

![](img/f0ff31812e93ed4785df1d52bdc08a0f_93.png)

![](img/f0ff31812e93ed4785df1d52bdc08a0f_94.png)

本节课中我们一起学习了智能指针的核心概念。我们探讨了宽指针如何包装动态类型，如何通过实现 `Deref` 和 `Drop` 特质来定制智能指针的行为，并深入了解了 `Rc<T>` 和 `RefCell<T>` 这两种允许共享所有权和内部可变性的智能指针。理解这些工具是编写安全、高效Rust程序的关键。下一讲，我们将进入多线程和异步编程的世界。