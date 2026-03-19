# 023：用户认证与Passport.js入门

![](img/522462dd3645ce38022515a28b7a2663_0.png)

在本节课中，我们将学习如何为全栈应用构建一个用户认证系统。我们将使用Node.js的Passport模块来处理授权和认证逻辑，并使用BCrypt来安全地哈希密码。此外，我们还将学习如何使用EJS（嵌入式JavaScript）进行服务器端HTML渲染。

## 概述

用户认证是验证用户凭据以访问非公开或受限数据的过程。本实验将指导我们构建一个基本的用户登录页面，涵盖从设置服务器到实现完整认证流程的多个步骤。我们将学习Passport.js、会话管理、受保护路由以及如何安全地存储用户密码。

## 设计阶段

在开始编码之前，我们先设计应用的基本视图和流程。这有助于明确所需的路线和控制器。

我们的应用将包含三个主要视图：
1.  **主页（受保护路由）**：用户登录后看到的个人资料页面，显示欢迎信息并提供注销选项。
2.  **注册页面（仅限未登录用户访问）**：包含姓名、邮箱和密码输入的表单。
3.  **登录页面（仅限未登录用户访问）**：包含邮箱和密码输入的表单。

## 项目初始化与基础服务器

首先，我们需要创建项目目录结构并初始化一个基础的Express服务器。

以下是项目初始化的步骤：
1.  创建项目目录 `user-login-app`。
2.  进入该目录并初始化 `package.json` 文件。
3.  创建主要的应用文件 `app.js`。
4.  创建组织代码的子目录：`controllers`、`middlewares`、`models`、`routes`、`views`。

在 `package.json` 中，我们定义项目信息并添加 `express` 作为初始依赖。

```json
{
  "name": "user-login-app",
  "version": "1.0.0",
  "description": "A project that implements user authentication using Passport.js",
  "main": "app.js",
  "scripts": {
    "start": "npm install && node app.js"
  },
  "author": "Your Name",
  "dependencies": {
    "express": "^4.18.2"
  }
}
```

在 `app.js` 中，我们设置一个监听端口的简单Express服务器。

```javascript
const express = require('express');
const app = express();
const port = 3000;

function setupApp() {
  // 中间件和路由设置将在这里进行
}

![](img/522462dd3645ce38022515a28b7a2663_2.png)

![](img/522462dd3645ce38022515a28b7a2663_3.png)

![](img/522462dd3645ce38022515a28b7a2663_4.png)

![](img/522462dd3645ce38022515a28b7a2663_6.png)

![](img/522462dd3645ce38022515a28b7a2663_8.png)

![](img/522462dd3645ce38022515a28b7a2663_10.png)

setupApp();
app.listen(port, () => {
  console.log(`Listening on port ${port}`);
});
```

![](img/522462dd3645ce38022515a28b7a2663_12.png)

![](img/522462dd3645ce38022515a28b7a2663_14.png)

运行 `npm start` 可以启动服务器并验证其是否正常工作。

![](img/522462dd3645ce38022515a28b7a2663_16.png)

## 使用EJS渲染服务器端HTML

上一节我们设置了基础服务器，本节中我们来看看如何使用EJS模板引擎来动态生成并发送HTML页面给客户端。

![](img/522462dd3645ce38022515a28b7a2663_18.png)

EJS允许我们在HTML中嵌入JavaScript逻辑，并在服务器端进行渲染。

![](img/522462dd3645ce38022515a28b7a2663_20.png)

以下是实现此目标的步骤：
1.  在 `package.json` 的依赖中添加 `ejs`。
2.  在 `app.js` 的 `setupApp` 函数中，将视图引擎设置为 `ejs`。
3.  在 `views` 目录下创建 `index.ejs` 文件作为主页模板。
4.  创建路由 (`routes/user-routes.js`) 和控制器 (`controllers/user-controller.js`) 来处理请求并渲染EJS模板。
5.  在控制器中，使用 `res.render('index.ejs', { name: 'data' })` 来渲染模板并传递数据。

![](img/522462dd3645ce38022515a28b7a2663_22.png)

![](img/522462dd3645ce38022515a28b7a2663_24.png)

![](img/522462dd3645ce38022515a28b7a2663_26.png)

在 `index.ejs` 中，我们可以使用 `<%= name %>` 语法来显示从服务器传递过来的数据。

![](img/522462dd3645ce38022515a28b7a2663_28.png)

```html
<h1>Hi <%= name %></h1>
```

![](img/522462dd3645ce38022515a28b7a2663_30.png)

![](img/522462dd3645ce38022515a28b7a2663_32.png)

启动服务器并访问主页，可以看到动态生成的“Hi data”内容。

![](img/522462dd3645ce38022515a28b7a2663_34.png)

![](img/522462dd3645ce38022515a28b7a2663_36.png)

![](img/522462dd3645ce38022515a28b7a2663_38.png)

## 设置登录与注册页面路由

![](img/522462dd3645ce38022515a28b7a2663_40.png)

![](img/522462dd3645ce38022515a28b7a2663_42.png)

![](img/522462dd3645ce38022515a28b7a2663_44.png)

![](img/522462dd3645ce38022515a28b7a2663_46.png)

现在我们已经能够渲染主页，接下来需要为登录和注册功能创建对应的页面和路由。

![](img/522462dd3645ce38022515a28b7a2663_48.png)

![](img/522462dd3645ce38022515a28b7a2663_50.png)

![](img/522462dd3645ce38022515a28b7a2663_52.png)

以下是创建登录和注册页面的步骤：
1.  在 `views` 目录下创建 `login.ejs` 和 `register.ejs` 文件。
2.  在用户控制器 (`user-controller.js`) 中，添加 `getLogin` 和 `getRegister` 方法，分别用于渲染登录和注册页面。
3.  在用户路由 (`user-routes.js`) 中，为 `/login` 和 `/register` 路径设置GET请求处理，并关联到上一步创建的控制器方法。
4.  在 `app.js` 中确保正确加载了用户路由。

![](img/522462dd3645ce38022515a28b7a2663_54.png)

完成这些步骤后，访问 `/login` 和 `/register` 路径就能看到对应的页面。

![](img/522462dd3645ce38022515a28b7a2663_56.png)

## 创建表单并处理POST请求

![](img/522462dd3645ce38022515a28b7a2663_58.png)

![](img/522462dd3645ce38022515a28b7a2663_59.png)

![](img/522462dd3645ce38022515a28b7a2663_61.png)

![](img/522462dd3645ce38022515a28b7a2663_63.png)

![](img/522462dd3645ce38022515a28b7a2663_65.png)

我们有了登录和注册页面的框架，现在需要在页面上添加表单，以便用户提交数据。

![](img/522462dd3645ce38022515a28b7a2663_67.png)

![](img/522462dd3645ce38022515a28b7a2663_69.png)

![](img/522462dd3645ce38022515a28b7a2663_71.png)

在 `register.ejs` 和 `login.ejs` 中，我们创建包含输入字段（如姓名、邮箱、密码）的HTML表单。表单的 `action` 属性指向相应的端点（如 `/register`），`method` 属性设置为 `post`。

![](img/522462dd3645ce38022515a28b7a2663_73.png)

![](img/522462dd3645ce38022515a28b7a2663_75.png)

![](img/522462dd3645ce38022515a28b7a2663_77.png)

![](img/522462dd3645ce38022515a28b7a2663_78.png)

为了在服务器端解析POST请求的正文数据，我们需要使用 `body-parser` 中间件。

![](img/522462dd3645ce38022515a28b7a2663_80.png)

![](img/522462dd3645ce38022515a28b7a2663_82.png)

以下是处理表单提交的步骤：
1.  Express 4.16+ 版本内置了 `express.json` 和 `express.urlencoded` 中间件，我们可以直接使用它们来代替独立的 `body-parser` 包。
2.  在 `app.js` 的 `setupApp` 函数中，通过 `app.use(express.urlencoded({ extended: false }))` 来启用URL编码数据的解析。
3.  在用户控制器中，创建 `postLogin` 和 `postRegister` 方法。在这些方法中，可以通过 `req.body` 访问表单提交的数据（例如 `req.body.email`, `req.body.password`）。
4.  在用户路由中，为 `/login` 和 `/register` 路径设置POST请求处理，并关联到新的控制器方法。

![](img/522462dd3645ce38022515a28b7a2663_84.png)

![](img/522462dd3645ce38022515a28b7a2663_86.png)

![](img/522462dd3645ce38022515a28b7a2663_88.png)

![](img/522462dd3645ce38022515a28b7a2663_90.png)

现在，当用户提交登录或注册表单时，服务器能够接收到数据并在控制台打印出来，同时返回一个“success”消息给客户端。

![](img/522462dd3645ce38022515a28b7a2663_92.png)

## 创建用户数据模型

![](img/522462dd3645ce38022515a28b7a2663_94.png)

![](img/522462dd3645ce38022515a28b7a2663_96.png)

![](img/522462dd3645ce38022515a28b7a2663_98.png)

当用户注册时，我们需要将他们的信息存储起来。本节我们将创建一个简单的内存数据模型来管理用户。

![](img/522462dd3645ce38022515a28b7a2663_100.png)

我们将使用 `shortid` 库为每个新用户生成唯一ID。

![](img/522462dd3645ce38022515a28b7a2663_102.png)

以下是创建用户模型的步骤：
1.  在 `package.json` 的依赖中添加 `shortid`。
2.  在 `models` 目录下创建 `user-model.js` 文件。
3.  在该文件中，定义一个 `Users` 类。这个类有一个 `users` 数组属性来存储所有用户，并有一个 `add` 方法用于接收姓名、邮箱和密码，生成ID后创建用户对象并推入数组。
4.  导出该类的一个实例。

![](img/522462dd3645ce38022515a28b7a2663_104.png)

在用户控制器的 `postRegister` 方法中，我们导入这个用户模型实例，并调用其 `add` 方法来存储新用户。注册成功后，将用户重定向到登录页面。

![](img/522462dd3645ce38022515a28b7a2663_106.png)

![](img/522462dd3645ce38022515a28b7a2663_108.png)

![](img/522462dd3645ce38022515a28b7a2663_110.png)

![](img/522462dd3645ce38022515a28b7a2663_112.png)

现在，当用户成功注册时，他们的信息会被添加到服务器的内存存储中。

![](img/522462dd3645ce38022515a28b7a2663_114.png)

## 使用Express Session管理客户端会话

![](img/522462dd3645ce38022515a28b7a2663_116.png)

![](img/522462dd3645ce38022515a28b7a2663_118.png)

![](img/522462dd3645ce38022515a28b7a2663_119.png)

为了识别来自同一客户端的连续请求，我们需要使用会话（Session）。Express Session 中间件会为每个客户端生成一个唯一的会话ID，并通过Cookie进行管理。

以下是设置会话的步骤：
1.  在 `package.json` 的依赖中添加 `express-session`。
2.  在 `app.js` 中导入 `express-session`。
3.  在 `setupApp` 函数中，配置会话选项（如密钥 `secret`）并使用该中间件。

![](img/522462dd3645ce38022515a28b7a2663_121.png)

配置完成后，每个请求对象 (`req`) 都会包含一个 `session` 属性。我们可以通过 `req.sessionID` 来查看当前会话的ID。通过测试可以发现，同一浏览器标签页的多次请求会共享相同的会话ID，而不同浏览器或隐身窗口则会有不同的ID。这为后续基于会话的用户认证打下了基础。

## 总结与下节预告

本节课中我们一起学习了构建用户认证系统的初始步骤。我们成功设置了项目结构、基础Express服务器，并利用EJS实现了服务器端HTML渲染。我们创建了登录和注册页面及其表单，能够接收并处理用户提交的POST数据。此外，我们还建立了一个内存中的用户数据模型来存储注册信息，并配置了Express Session来管理客户端会话。

![](img/522462dd3645ce38022515a28b7a2663_123.png)

在下一节课中，我们将在此基础上继续深入。我们将学习如何使用Passport.js来验证用户的登录凭据，如何序列化和反序列化用户信息，以及如何使用Flash消息在请求间传递临时信息。我们还将实现路由保护，确保只有登录用户才能访问主页，而未登录用户只能访问登录和注册页。最后，我们会使用BCrypt来安全地哈希存储密码，并使用dotenv来管理敏感的环境变量。这将使我们完成一个功能完整的用户认证系统。