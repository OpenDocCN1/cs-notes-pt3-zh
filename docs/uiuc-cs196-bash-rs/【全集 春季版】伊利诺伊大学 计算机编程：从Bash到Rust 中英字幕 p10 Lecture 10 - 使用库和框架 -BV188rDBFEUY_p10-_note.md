# 计算机编程：从Bash到Rust：10：使用库和框架 📚

在本节课中，我们将要学习库与框架的区别，以及如何在项目中实际使用它们。我们将探讨为什么开发者普遍使用这些工具，并学习如何评估和选择适合自己项目的库。

## 概述

上一节我们介绍了API（应用程序编程接口），它是一种通过网络与不同服务（如谷歌地图）交互以获取数据和使用功能的好方法。本节中，我们来看看另外两种避免“重复造轮子”的重要工具：库和框架。

## 库与框架的区别

首先，我们来明确库和框架的核心区别。

*   **库** 提供一组辅助函数、对象或模块，你的应用程序代码可以调用它们来实现特定功能。
    *   **示例**：一个提供统计功能的库，它可能包含计算列表平均值的函数。
    *   **代码示例**：`mean = statistics.mean(data_list)`
*   **框架** 定义了一些开放或未实现的函数或对象，用户通过编写代码来填充这些“骨架”，从而创建自定义应用程序。
    *   **示例**：Angular 是一个用于构建Web应用的JavaScript框架。它提供了一个基础结构，你只需在其中实现具体功能。

简而言之，库是**你调用它**的工具，而框架是**它调用你**的代码的结构。

## 如何在项目中使用库和框架

了解了基本概念后，我们来看看如何在个人项目中开始使用库和框架。以下是研究和引入新工具的一般步骤。

### 第一步：研究

首先，你需要进行研究。如果你需要一个实现特定功能的库，可以打开搜索引擎。

*   **方法**：搜索你需要的功能和你计划使用的编程语言。
*   **目标**：找到几个看起来有潜力的候选库或框架。

![](img/cdb3dd3eed1ed2ed7b9d7e8dbb02296e_1.png)

### 第二步：评估

![](img/cdb3dd3eed1ed2ed7b9d7e8dbb02296e_3.png)

找到几个候选后，下一步是评估哪个最适合你的项目。以下是一些有用的评估指标：

以下是评估库质量的几个关键指标：

1.  **GitHub星标数**：通常，星标越多，代表项目越受欢迎、越可靠。公式上可以简单理解为：`受欢迎度 ∝ 星标数`。
2.  **README文件**：README是项目的“门面”。一个清晰、美观、包含示例代码的README通常意味着项目本身质量较高。
3.  **文档**：快速浏览库的文档。检查它是否有示例代码、是否易于理解、语法你是否喜欢。
4.  **支持与维护**：查看GitHub仓库的“Issues”标签。观察已关闭和未解决问题的比例。一个健康维护的项目会及时响应和解决问题。
5.  **个人经验与偏好**：如果你之前用过类似的工具，可以优先考虑。有时选择也取决于个人编码风格偏好。

### 第三步：尝试

![](img/cdb3dd3eed1ed2ed7b9d7e8dbb02296e_5.png)

![](img/cdb3dd3eed1ed2ed7b9d7e8dbb02296e_7.png)

评估之后，就可以动手尝试了。

![](img/cdb3dd3eed1ed2ed7b9d7e8dbb02296e_8.png)

![](img/cdb3dd3eed1ed2ed7b9d7e8dbb02296e_10.png)

*   **方法**：将库引入你的项目（如果使用版本控制，建议新建分支），尝试实现一个简单的“Hello World”功能。
*   **目标**：感受一下使用体验。如果喜欢，就将其集成到你的主要项目中。

![](img/cdb3dd3eed1ed2ed7b9d7e8dbb02296e_12.png)

## 实践示例：在Rust项目中添加库

![](img/cdb3dd3eed1ed2ed7b9d7e8dbb02296e_14.png)

![](img/cdb3dd3eed1ed2ed7b9d7e8dbb02296e_16.png)

上一节我们介绍了评估库的通用方法，本节中我们来看看在Rust项目中具体如何操作。我们将以添加一个统计库为例。

![](img/cdb3dd3eed1ed2ed7b9d7e8dbb02296e_18.png)

![](img/cdb3dd3eed1ed2ed7b9d7e8dbb02296e_20.png)

假设我们需要一个Rust的统计库。我们可以访问 `crates.io`（Rust的包仓库网站）进行搜索。

搜索“statistics”后，我们可能找到几个候选，例如：
*   `stats-rs` (156 stars)
*   `rustats` (54 stars)
*   `statistic` (19 stars)

根据星标、README质量和Issues处理情况，我们决定尝试 `stats-rs`。

### 1. 添加依赖

在Rust中，我们使用Cargo管理依赖。所有依赖项在 `Cargo.toml` 文件的 `[dependencies]` 部分声明。

![](img/cdb3dd3eed1ed2ed7b9d7e8dbb02296e_22.png)

![](img/cdb3dd3eed1ed2ed7b9d7e8dbb02296e_24.png)

![](img/cdb3dd3eed1ed2ed7b9d7e8dbb02296e_25.png)

```toml
[dependencies]
stats-rs = "0.12.0"
```
版本号 `0.12.0` 通常可以在库的README“Getting Started”部分找到。

![](img/cdb3dd3eed1ed2ed7b9d7e8dbb02296e_27.png)

![](img/cdb3dd3eed1ed2ed7b9d7e8dbb02296e_29.png)

### 2. 下载依赖

在终端中运行 `cargo build` 命令。Cargo会自动下载 `stats-rs` 及其所有依赖项（依赖的依赖），形成一个依赖关系图并全部安装。

### 3. 在代码中使用

![](img/cdb3dd3eed1ed2ed7b9d7e8dbb02296e_31.png)

![](img/cdb3dd3eed1ed2ed7b9d7e8dbb02296e_32.png)

依赖安装好后，需要在代码中引入才能使用其功能。

![](img/cdb3dd3eed1ed2ed7b9d7e8dbb02296e_34.png)

```rust
// 引入整个crate（库）
extern crate stats_rs;

![](img/cdb3dd3eed1ed2ed7b9d7e8dbb02296e_36.png)

![](img/cdb3dd3eed1ed2ed7b9d7e8dbb02296e_38.png)

// 从stats_rs的statistics模块中，引入mean和median这两个特定函数
use stats_rs::statistics::{mean, median};

![](img/cdb3dd3eed1ed2ed7b9d7e8dbb02296e_40.png)

fn main() {
    let data = vec![1.0, 2.0, 3.0, 4.0, 5.0];
    let m = mean(&data);
    println!("The mean is: {}", m);
}
```
**注意**：使用 `use` 语句精确导入所需功能，而不是导入整个库，这可以避免命名空间污染，并使代码更清晰。

![](img/cdb3dd3eed1ed2ed7b9d7e8dbb02296e_42.png)

![](img/cdb3dd3eed1ed2ed7b9d7e8dbb02296e_43.png)

![](img/cdb3dd3eed1ed2ed7b9d7e8dbb02296e_45.png)

### 4. 查阅文档与测试

你可以随时查阅库的在线文档，复制示例代码到你的项目中进行测试和修改。同时，确保你选择的库有良好的社区支持（即Issues能被及时响应和关闭），这对长期项目至关重要。

![](img/cdb3dd3eed1ed2ed7b9d7e8dbb02296e_47.png)

![](img/cdb3dd3eed1ed2ed7b9d7e8dbb02296e_49.png)

![](img/cdb3dd3eed1ed2ed7b9d7e8dbb02296e_51.png)

![](img/cdb3dd3eed1ed2ed7b9d7e8dbb02296e_53.png)

![](img/cdb3dd3eed1ed2ed7b9d7e8dbb02296e_55.png)

## 包管理器简介

![](img/cdb3dd3eed1ed2ed7b9d7e8dbb02296e_57.png)

![](img/cdb3dd3eed1ed2ed7b9d7e8dbb02296e_59.png)

![](img/cdb3dd3eed1ed2ed7b9d7e8dbb02296e_60.png)

![](img/cdb3dd3eed1ed2ed7b9d7e8dbb02296e_62.png)

需要指出的是，不仅仅是Rust，大多数现代编程语言都有类似的包管理工具：

*   **Rust**: Cargo (`cargo build`)
*   **JavaScript/Node.js**: npm (`npm install`)
*   **Python**: pip (`pip install`)
*   **Java**: Maven, Gradle

它们的功能类似：帮助你声明、下载和管理项目所依赖的库。

## 总结与展望 🧑‍🍳

本节课中我们一起学习了库与框架的核心区别，掌握了从研究、评估到实际集成一个库的完整流程，并具体实践了如何在Rust项目中使用Cargo添加外部依赖。

可以将软件开发想象成烹饪。一位优秀的厨师（开发者）不会从种小麦、养奶牛开始做一顿饭（项目）。他会利用市场上优质的食材（库）和高效的厨具（框架），将它们组合起来，创造出美味佳肴（软件）。现代软件开发很大程度上正是如此：识别需求，寻找并集成现有的优秀工具，快速构建出功能强大的应用。

![](img/cdb3dd3eed1ed2ed7b9d7e8dbb02296e_64.png)

在你们未来的项目和职业生涯中，请积极运用这种思维。从你的课程项目开始，尝试研究有哪些库可以让你的开发过程更高效、让你的应用功能更出色。