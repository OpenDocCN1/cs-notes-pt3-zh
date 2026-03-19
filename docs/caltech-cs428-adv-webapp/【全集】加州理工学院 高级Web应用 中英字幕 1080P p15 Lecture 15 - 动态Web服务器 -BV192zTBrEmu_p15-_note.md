# 高级Web应用：第15讲：动态Web服务器 🚀

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_0.png)

在本节课中，我们将学习如何使用Express框架构建一个动态Web服务器。我们将从设置项目开始，逐步实现一个能够响应GET和POST请求、提供HTML文件、处理表单数据并返回JSON响应的服务器。最后，我们将学习如何将应用部署到Heroku平台，使其在互联网上公开可用。

## 概述 📋

上一节我们介绍了静态Web服务器，它只负责向客户端返回HTML文档。本节中，我们将转向动态Web服务器。动态服务器不仅能提供HTML内容，还能处理业务逻辑、响应不同的HTTP方法（如GET、POST），并维护服务器端的数据。我们将使用Express框架来简化这一过程，并最终将应用部署到Heroku。

## 迭代一：使用NPM设置Express应用 📦

首先，我们需要设置一个Express应用。由于Express不是Node.js的核心模块，我们需要使用NPM（Node包管理器）来安装它。这需要一个配置文件来管理应用的依赖项和启动命令。

以下是创建和配置`package.json`文件的步骤：

1.  在项目根目录下创建`package.json`文件。
2.  在文件中定义应用的基本元数据，如名称、版本、描述和入口点。
3.  在`dependencies`对象中指定需要安装的包及其版本。

```json
{
  "name": "web-server",
  "version": "1.0.0",
  "description": "A dynamic web server using Express",
  "main": "app.js",
  "author": "Your Name",
  "dependencies": {
    "express": "*"
  }
}
```

创建好`package.json`后，在终端运行`npm install`命令。NPM会读取该文件，自动下载并安装Express及其所有依赖项到`node_modules`文件夹中。

## 迭代二：创建发送响应的服务器 💬

现在，我们将创建一个基本的Express服务器，它能够监听请求并发送一个简单的“Hello World”响应。

以下是实现步骤：

1.  创建主应用文件`app.js`。
2.  导入`express`模块并创建Express应用实例。
3.  定义一个端口号（例如3000）。
4.  设置一个路由，监听根路径（`/`）的GET请求，并绑定一个处理函数。
5.  在处理函数中，使用`response.send()`方法向客户端发送“Hello World”消息。
6.  最后，让应用开始监听指定的端口。

```javascript
// 导入express模块
const express = require('express');
// 创建Express应用实例
const app = express();
// 定义端口
const port = 3000;

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_2.png)

// 定义根路径的GET请求处理函数
function serveIndex(request, response) {
  response.send('Hello World');
}

// 设置路由：当收到对根路径的GET请求时，调用serveIndex函数
app.get('/', serveIndex);

// 启动服务器，开始监听指定端口
app.listen(port, () => {
  console.log(`Server is running on port ${port}`);
});
```

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_4.png)

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_6.png)

运行`node app.js`启动服务器，然后在浏览器中访问`http://localhost:3000`，你应该能看到“Hello World”消息。

## 迭代三：创建提供HTML文件的服务器 📄

接下来，我们将改进服务器，使其能够向客户端发送一个HTML文件，而不仅仅是纯文本。

以下是实现步骤：

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_8.png)

1.  在项目目录中创建一个`index.html`文件，并编写一些简单的HTML内容。
2.  修改`app.js`中的`serveIndex`处理函数。
3.  使用`response.sendFile()`方法替代`response.send()`。该方法需要两个参数：要发送的文件名和一个指定根目录的选项对象。
4.  使用Node.js的`__dirname`全局变量来获取当前文件所在的目录路径，作为文件的根目录。

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_10.png)

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_12.png)

```javascript
// 修改serveIndex函数以发送HTML文件
function serveIndex(request, response) {
  response.sendFile('index.html', { root: __dirname });
}

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_14.png)

// 路由设置保持不变
app.get('/', serveIndex);
```

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_16.png)

重启服务器并刷新浏览器，现在你应该能看到`index.html`文件的内容被正确渲染。

## 迭代四：提供另一个HTML文件 🔗

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_18.png)

一个完整的网站通常有多个页面。现在，我们将创建第二个页面（例如一个联系表单页面），并设置路由来提供它。

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_20.png)

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_22.png)

以下是实现步骤：

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_24.png)

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_26.png)

1.  创建一个新的HTML文件，例如`contact.html`，并在其中构建一个表单。
2.  在`app.js`中，为`/contact.html`路径设置一个新的GET路由。
3.  创建一个新的处理函数（例如`serveContact`），用于发送`contact.html`文件。

```html
<!-- contact.html 示例 -->
<form method="POST" action="/contact/send">
  <input type="text" name="name" placeholder="Enter name">
  <input type="email" name="email" placeholder="Enter email">
  <textarea name="message" placeholder="Enter message"></textarea>
  <button type="submit">Submit</button>
</form>
```

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_28.png)

```javascript
// 新增处理函数，用于发送联系页面
function serveContact(request, response) {
  response.sendFile('contact.html', { root: __dirname });
}

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_30.png)

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_32.png)

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_33.png)

// 为联系页面设置新的GET路由
app.get('/contact.html', serveContact);
```

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_35.png)

现在，访问`http://localhost:3000/contact.html`就能看到联系表单页面。

## 迭代五：设置POST路由 📤

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_37.png)

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_39.png)

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_40.png)

我们的联系表单设置了`method="POST"`和`action="/contact/send"`。现在，我们需要在服务器端设置相应的路由来处理这个POST请求。

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_42.png)

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_44.png)

以下是实现步骤：

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_46.png)

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_48.png)

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_50.png)

1.  在`app.js`中，为`/contact/send`路径设置一个POST路由。
2.  创建一个新的处理函数（例如`contactHandler`）。
3.  在这个处理函数中，我们暂时只在服务器终端打印一条消息，然后将客户端重定向回首页。

```javascript
// 新增处理函数，用于处理表单提交
function contactHandler(request, response) {
  console.log('Received a POST request');
  response.redirect('/'); // 重定向回首页
}

// 为表单提交设置POST路由
app.post('/contact/send', contactHandler);
```

填写联系表单并提交后，你会在运行服务器的终端看到“Received a POST request”的日志，并且浏览器会被重定向到首页。

## 迭代六：解析POST请求中的查询字符串 🔍

表单数据通常以查询字符串的形式在POST请求体中发送。为了在服务器端访问这些数据，我们需要使用一个名为`body-parser`的中间件。

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_52.png)

以下是实现步骤：

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_54.png)

1.  使用NPM安装`body-parser`模块：`npm install body-parser`。
2.  在`app.js`顶部导入`body-parser`。
3.  在设置任何路由**之前**，通过`app.use()`告诉Express应用使用`body-parser`的JSON和URL编码解析器。
4.  修改`contactHandler`函数，通过`request.body`来访问解析后的表单数据。

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_56.png)

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_58.png)

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_60.png)

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_62.png)

```javascript
// 导入body-parser模块
const bodyParser = require('body-parser');

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_64.png)

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_66.png)

// 在设置路由前，使用body-parser中间件
app.use(bodyParser.json());
app.use(bodyParser.urlencoded({ extended: true }));

// 修改contactHandler函数以查看请求体
function contactHandler(request, response) {
  console.log(request.body); // 打印表单数据
  response.redirect('/');
}
```

现在，当你提交表单时，服务器终端会打印出一个包含`name`、`email`和`message`字段的对象。

## 迭代七：创建GET路由以返回JSON数据 📊

我们已经可以接收数据，现在让我们创建一个新的端点，允许客户端通过GET请求获取所有已提交的表单数据。

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_68.png)

以下是实现步骤：

1.  在`app.js`顶部创建一个数组（例如`submissions`）来存储提交的数据。
2.  修改`contactHandler`函数，将每次收到的`request.body`对象推入`submissions`数组。
3.  创建一个新的GET路由，例如`/submissions`。
4.  为该路由创建一个处理函数（例如`serveSubmissions`），使用`response.json()`方法将`submissions`数组作为JSON数据发送给客户端。

```javascript
// 用于存储提交数据的数组
let submissions = [];

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_70.png)

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_72.png)

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_74.png)

// 修改contactHandler，存储数据
function contactHandler(request, response) {
  submissions.push(request.body); // 将新数据存入数组
  response.redirect('/');
}

// 新增处理函数，用于返回所有提交的数据
function serveSubmissions(request, response) {
  response.json(submissions); // 以JSON格式发送数组
}

// 设置获取提交数据的GET路由
app.get('/submissions', serveSubmissions);
```

现在，访问`http://localhost:3000/submissions`，你会看到一个包含所有已提交表单数据的JSON数组。你甚至可以在客户端JavaScript中使用`fetch` API来获取这些数据。

## 迭代八：使用Heroku部署应用 ☁️

最后，我们将把这个动态Web服务器部署到互联网上，使用Heroku的免费云服务。

以下是部署步骤：

1.  **准备生产环境配置**：
    *   修改端口设置，使其能适应Heroku动态分配的环境变量。
    *   确保导入了Node.js的`path`模块（如果`sendFile`需要）。
    *   在`package.json`中添加一个`scripts`部分，定义启动命令。

    ```javascript
    // 动态设置端口：优先使用Heroku提供的端口，否则使用3000
    const port = process.env.PORT || 3000;
    ```

    ```json
    // 在package.json中添加启动脚本
    "scripts": {
      "start": "npm install && node app.js"
    }
    ```

2.  **安装Heroku CLI并登录**：
    *   根据Heroku文档安装命令行工具。
    *   在终端运行`heroku login`并完成浏览器登录。

3.  **创建Heroku应用**：
    *   在项目目录下，运行`heroku create`。这会创建一个随机的应用名并关联到你的Heroku账户。

4.  **初始化Git并关联Heroku**：
    *   如果项目还不是Git仓库，运行`git init`。
    *   运行`git remote add heroku <你的Heroku应用Git URL>`。Heroku CLI通常会自动设置好。

5.  **创建.gitignore文件**：
    *   运行`echo node_modules > .gitignore`，确保不将本地的依赖包上传到Heroku。

6.  **提交并推送代码**：
    *   运行`git add .`和`git commit -m "Initial commit"`。
    *   运行`git push heroku master`。Heroku会自动构建和部署你的应用。

部署成功后，Heroku会提供一个URL（如`https://your-app-name.herokuapp.com`）。访问这个URL，你的动态Web应用就在公网可用了！

## 总结 🎉

在本节课中，我们一起学习了如何使用Express框架构建一个动态Web服务器。我们从设置项目和基本响应开始，逐步实现了提供HTML文件、处理表单POST请求、解析数据、以及通过API端点返回JSON数据的功能。最后，我们成功地将应用部署到了Heroku平台，使其成为一个真正的在线服务。

关键知识点包括：
*   **Express框架**：简化了路由设置和请求处理。
*   **中间件**：如`body-parser`，用于在请求到达路由处理函数前进行预处理。
*   **REST端点**：服务器端设置URL路径来响应不同的HTTP方法。
*   **数据流**：客户端通过表单POST数据到服务器，服务器存储数据并通过另一个GET端点提供数据。
*   **部署**：使用Git和Heroku CLI将Node.js应用部署到云端。

![](img/bb0d34d5369a7f8d2f73cd3eb71961cb_76.png)

这个动态服务器为构建更复杂的Web应用（如需要用户认证、数据库集成或实时功能的应用）奠定了基础。