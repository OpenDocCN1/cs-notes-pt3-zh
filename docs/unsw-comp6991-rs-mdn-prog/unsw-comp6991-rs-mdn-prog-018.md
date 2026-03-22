# 018：Rust Async实战

![](img/ca8e9cfb69a280d42360d68e547db45c_0.png)

![](img/ca8e9cfb69a280d42360d68e547db45c_2.png)

![](img/ca8e9cfb69a280d42360d68e547db45c_3.png)

![](img/ca8e9cfb69a280d42360d68e547db45c_5.png)

![](img/ca8e9cfb69a280d42360d68e547db45c_7.png)

![](img/ca8e9cfb69a280d42360d68e547db45c_9.png)

在本节课中，我们将学习Rust异步编程的实际应用，特别是如何使用`tokio`运行时和`rocket`框架构建一个简单的Web服务。我们将创建一个类似Pastebin的文本分享服务，涵盖创建和检索文本片段的功能。

![](img/ca8e9cfb69a280d42360d68e547db45c_11.png)

![](img/ca8e9cfb69a280d42360d68e547db45c_13.png)

![](img/ca8e9cfb69a280d42360d68e547db45c_15.png)

---

## 课程回顾

![](img/ca8e9cfb69a280d42360d68e547db45c_17.png)

![](img/ca8e9cfb69a280d42360d68e547db45c_19.png)

上一节我们介绍了`Future`特质，它是Rust中表示并发操作的抽象。与JavaScript的`Promise`不同，Rust的`Future`需要被主动轮询（`poll`）才能推进工作。这种设计体现了Rust对性能成本的显式控制理念。

本节中，我们将看看如何在实际项目中应用这些概念，而不必直接与底层的`Future`特质交互。

![](img/ca8e9cfb69a280d42360d68e547db45c_21.png)

![](img/ca8e9cfb69a280d42360d68e547db45c_23.png)

---

## 异步运行时：Tokio

在编写异步代码时，我们通常依赖一个**执行器**（Executor）来调度和推进`Future`。`tokio`是Rust生态中最流行的异步运行时之一。

*   **高效IO处理**：`tokio`针对IO密集型任务进行了高度优化。它使用像`epoll`（Linux）这样的系统调用，可以在单个或少量操作系统线程上高效地管理成千上万个并发连接。
*   **重新实现标准库**：`tokio`提供了异步版本的许多标准库功能（如文件读写、网络操作），这些操作返回`Future`，可以被`tokio`高效地调度。
*   **与线程的对比**：对于CPU密集型任务，使用`tokio`可能不是最佳选择，此时应考虑使用`rayon`这类专注于数据并行的库。`tokio`更适合处理大量等待IO的操作。

以下是一个在`tokio`中创建文件的异步代码示例：
```rust
use tokio::fs::File;

async fn create_file_example() -> std::io::Result<()> {
    let mut file = File::create("hello.txt").await?;
    // 对文件进行异步操作...
    Ok(())
}
```

---

## Web框架：Rocket

![](img/ca8e9cfb69a280d42360d68e547db45c_25.png)

![](img/ca8e9cfb69a280d42360d68e547db45c_27.png)

`Rocket`是一个使编写Rust Web服务变得非常简单的框架。它构建在`tokio`之上，并充分利用了Rust的类型系统来保证安全。

![](img/ca8e9cfb69a280d42360d68e547db45c_29.png)

![](img/ca8e9cfb69a280d42360d68e547db45c_31.png)

*   **简洁的API**：通过过程宏（如`#[get]`）来定义路由，代码清晰直观。
*   **请求守卫**：这是`Rocket`的一大特色。它允许你利用Rust的类型系统，在请求到达处理函数之前，就对参数进行验证和转换。

例如，我们可以定义一个`PasteId`类型，确保路由参数是一个有效的UUID：
```rust
use rocket::request::FromParam;
use uuid::Uuid;

![](img/ca8e9cfb69a280d42360d68e547db45c_33.png)

![](img/ca8e9cfb69a280d42360d68e547db45c_34.png)

struct PasteId(Uuid);

![](img/ca8e9cfb69a280d42360d68e547db45c_36.png)

![](img/ca8e9cfb69a280d42360d68e547db45c_38.png)

impl<'a> FromParam<'a> for PasteId {
    type Error = &'static str;

    fn from_param(param: &'a str) -> Result<Self, Self::Error> {
        Uuid::parse_str(param)
            .map(PasteId)
            .map_err(|_| "无效的 Paste ID")
    }
}

![](img/ca8e9cfb69a280d42360d68e547db45c_40.png)

![](img/ca8e9cfb69a280d42360d68e547db45c_41.png)

![](img/ca8e9cfb69a280d42360d68e547db45c_43.png)

![](img/ca8e9cfb69a280d42360d68e547db45c_45.png)

![](img/ca8e9cfb69a280d42360d68e547db45c_47.png)

![](img/ca8e9cfb69a280d42360d68e547db45c_48.png)

![](img/ca8e9cfb69a280d42360d68e547db45c_50.png)

#[get("/<id>")]
async fn retrieve_paste(id: PasteId) -> Option<File> {
    // `id` 在这里已经被验证为有效的UUID
    // ... 打开文件等操作
}
```
通过这种方式，无效的ID会在进入业务逻辑之前就被拦截，并返回`404`错误。

![](img/ca8e9cfb69a280d42360d68e547db45c_52.png)

![](img/ca8e9cfb69a280d42360d68e547db45c_53.png)

---

## 实战：构建Pastebin服务

现在，我们将结合所学，构建一个简易的文本分享服务。

### 项目设置

首先，添加必要的依赖到`Cargo.toml`：
```toml
[dependencies]
rocket = "0.5.0-rc.2"
tokio = { version = "1", features = ["full"] }
uuid = { version = "1", features = ["v4", "serde"] }
serde = { version = "1", features = ["derive"] }
```

### 核心功能实现

以下是实现创建和检索`paste`的两个核心路由：

1.  **创建Paste**：接收POST请求和文本数据，生成一个唯一的ID，并将内容保存到文件。
    ```rust
    use rocket::data::{Data, ToByteUnit};
    use rocket::http::Status;
    use uuid::Uuid;

    #[post("/create", data = "<paste>")]
    async fn create_paste(paste: Data<'_>) -> Result<String, Status> {
        // 1. 生成唯一ID
        let id = Uuid::new_v4();
        let file_path = format!("./pastes/{}", id);

        // 2. 异步打开文件
        let mut file = File::create(&file_path)
            .await
            .map_err(|_| Status::InternalServerError)?;

        // 3. 将请求体数据流异步写入文件（限制大小）
        paste
            .open(512.kibibytes())
            .stream_to(&mut file)
            .await
            .map_err(|_| Status::PayloadTooLarge)?;

        // 4. 返回生成的ID
        Ok(id.to_string())
    }
    ```

2.  **检索Paste**：根据URL中的ID，读取对应的文件并返回内容。
    ```rust
    use rocket::response::content;

    #[get("/<id>")]
    async fn get_paste(id: PasteId) -> Option<content::Plain<File>> {
        // 1. 将ID转换为文件路径
        let file_path = id.to_file_path();

        // 2. 异步打开文件
        File::open(file_path)
            .await
            .ok()
            .map(content::Plain)
    }
    ```

### 启动应用

![](img/ca8e9cfb69a280d42360d68e547db45c_55.png)

![](img/ca8e9cfb69a280d42360d68e547db45c_57.png)

最后，使用`#[rocket::main]`宏启动我们的异步应用：
```rust
#[rocket::main]
async fn main() -> Result<(), rocket::Error> {
    rocket::build()
        .mount("/", routes![create_paste, get_paste])
        .launch()
        .await?;

    Ok(())
}
```

![](img/ca8e9cfb69a280d42360d68e547db45c_59.png)

---

![](img/ca8e9cfb69a280d42360d68e547db45c_61.png)

![](img/ca8e9cfb69a280d42360d68e547db45c_63.png)

![](img/ca8e9cfb69a280d42360d68e547db45c_65.png)

![](img/ca8e9cfb69a280d42360d68e547db45c_67.png)

![](img/ca8e9cfb69a280d42360d68e547db45c_69.png)

## 总结

![](img/ca8e9cfb69a280d42360d68e547db45c_71.png)

![](img/ca8e9cfb69a280d42360d68e547db45c_73.png)

本节课我们一起学习了Rust异步编程的实战应用。我们了解到：
1.  **`tokio`运行时** 负责高效调度和执行异步任务，特别适合IO密集型应用。
2.  **`rocket`框架** 提供了构建Web服务的高级抽象，其“请求守卫”等功能巧妙地利用Rust类型系统提升了安全性与代码健壮性。
3.  通过构建一个简单的Pastebin服务，我们实践了如何定义异步路由、处理数据流、进行文件IO，并最终运行一个并发性能优异的Web服务。

![](img/ca8e9cfb69a280d42360d68e547db45c_75.png)

![](img/ca8e9cfb69a280d42360d68e547db45c_77.png)

![](img/ca8e9cfb69a280d42360d68e547db45c_79.png)

![](img/ca8e9cfb69a280d42360d68e547db45c_81.png)

![](img/ca8e9cfb69a280d42360d68e547db45c_83.png)

Rust的异步生态仍在快速发展，虽然一些高级特性（如异步特质方法）尚未完全稳定，但现有的工具链已经足够强大，能够用于构建高性能、可靠的后端服务。