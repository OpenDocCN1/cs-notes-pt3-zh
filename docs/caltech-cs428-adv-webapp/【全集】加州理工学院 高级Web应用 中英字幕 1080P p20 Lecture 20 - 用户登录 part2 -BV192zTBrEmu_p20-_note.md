# WebSocket 与 Socket.IO 入门教程：20：构建实时聊天应用

![](img/9cfac7f54709a60a64f397cb3bb38731_0.png)

在本节课中，我们将学习 WebSocket 协议以及如何使用 Socket.IO 库在 Node.js 和浏览器之间建立实时、双向的通信。我们将通过构建一个基础的实时聊天应用来实践这些概念。

## 概述

WebSocket 是一种不同于 HTTP 的通信协议，它允许在客户端和服务器之间建立持久、全双工的连接。这使得服务器可以主动向客户端推送数据，非常适合构建聊天应用、实时游戏或数据仪表盘等场景。Socket.IO 是一个 JavaScript 库，它封装了 WebSocket 协议，并提供了更简单、更强大的 API 来处理实时通信。

## 1. 核心概念介绍

上一节我们概述了课程目标，本节中我们来看看构建实时应用所需理解的核心概念。

### 1.1 WebSocket 协议

WebSocket 协议是 HTTP 协议的替代方案，用于客户端与服务器之间的通信。它与 HTTP 的关键区别在于：

*   **连接性质**：HTTP 是无状态、非持久的连接。每次通信都需要客户端发起一个新的请求，服务器响应后连接即断开。这就像**发送信件**。
*   **通信方向**：WebSocket 是**全双工、双向**的持久连接。一旦建立，客户端和服务器都可以随时主动发送或接收数据。这就像**接打电话**。

在 WebSocket 出现之前，为了实现“实时”效果，客户端需要不断向服务器发送请求以检查是否有新数据，这种方式称为“轮询”。轮询效率低下且浪费资源。WebSocket 解决了这个问题，允许服务器在数据变化时立即广播给所有已连接的客户端。

### 1.2 Socket.IO 库

Socket.IO 是一个实现了 WebSocket 协议的 JavaScript 库。它简化了在浏览器和 Node.js 服务器中使用 WebSocket 的复杂性，并自动处理了连接稳定性、断线重连等底层细节。使用 Socket.IO 需要在服务器端和客户端都进行设置。

### 1.3 事件驱动通信

Socket.IO 的核心是**事件驱动**的通信模型。通信双方（客户端或服务器）可以**发射（emit）** 命名事件，并附带数据。另一方则可以**监听（on）** 这些事件，并绑定回调函数来处理它们。

**事件发射的基本语法**：
```javascript
// 发射一个事件，附带数据
socket.emit(‘事件名称‘, 数据负载);
```

**事件监听的基本语法**：
```javascript
// 监听一个事件，并定义处理函数
socket.on(‘事件名称‘, (数据负载) => {
    // 处理接收到的事件和数据
});
```

数据负载通常以 **JSON** 格式传输，因为它易于序列化和反序列化，并且在 JavaScript 环境中可以直接作为对象使用。

### 1.4 应用设计模式

在设计分布式实时应用时，可以考虑以下模式：

*   **服务器角色**：通常作为“单一数据源”，维护应用的**真实状态**。它负责接收来自某个客户端的更新，然后将状态变更**广播**给所有其他连接的客户端。
*   **客户端角色**：提供用户界面和交互。当用户操作改变状态时，客户端向服务器**发射事件**。客户端不应直接更新本地状态并显示，而应等待服务器广播的更新，以确保所有用户视图同步。

## 2. 项目初始化与结构

理解了核心概念后，我们开始动手构建项目。首先需要设置项目的基本结构。

以下是创建项目目录和文件的步骤：

![](img/9cfac7f54709a60a64f397cb3bb38731_2.png)

1.  创建一个项目根目录，例如 `chat-app`。
2.  在根目录下创建 `package.json` 文件，用于管理项目依赖和脚本。
3.  创建 `app.js` 文件，作为服务器的主逻辑文件。
4.  创建一个 `public` 目录，用于存放所有提供给客户端的静态文件（HTML, CSS, JS）。
5.  在 `public` 目录下创建 `index.html` 文件。
6.  在 `public` 目录下创建 `scripts` 目录，用于存放客户端 JavaScript 文件。
7.  在 `public/scripts` 目录下创建 `chat.js` 文件。

最终目录结构应如下所示：
```
chat-app/
├── app.js
├── package.json
├── node_modules/
└── public/
    ├── index.html
    └── scripts/
        └── chat.js
```

![](img/9cfac7f54709a60a64f397cb3bb38731_4.png)

## 3. 配置项目与 Express 服务器

现在我们已经有了项目骨架，本节将配置项目依赖并搭建一个基础的 Express 静态服务器。

![](img/9cfac7f54709a60a64f397cb3bb38731_6.png)

### 3.1 配置 package.json

首先，编辑 `package.json` 文件，定义项目元信息和依赖。

![](img/9cfac7f54709a60a64f397cb3bb38731_8.png)

```json
{
  “name“: “socket-chat-app“,
  “version“: “0.0.1“,
  “description“: “A real-time chat app with Socket.IO“,
  “main“: “app.js“,
  “scripts“: {
    “start“: “node app.js“
  },
  “dependencies“: {
    “express“: “^4.18.2“
  }
}
```

![](img/9cfac7f54709a60a64f397cb3bb38731_10.png)

然后，在终端中进入项目根目录，运行以下命令安装依赖：
```bash
npm install
```
此命令会根据 `package.json` 安装 Express，并生成 `node_modules` 文件夹及 `package-lock.json` 文件。

### 3.2 创建基础 Express 服务器

![](img/9cfac7f54709a60a64f397cb3bb38731_12.png)

![](img/9cfac7f54709a60a64f397cb3bb38731_14.png)

接下来，在 `app.js` 中设置一个基本的 Express 服务器，用于托管静态文件。注意，为了后续集成 WebSocket，我们创建服务器的方式略有不同。

![](img/9cfac7f54709a60a64f397cb3bb38731_16.png)

```javascript
// 导入所需模块
const express = require(‘express‘);
const http = require(‘http‘); // 需要 http 模块来创建服务器

// 初始化 Express 应用
const app = express();
// 使用 http 模块基于 Express 应用创建服务器
const server = http.createServer(app);

![](img/9cfac7f54709a60a64f397cb3bb38731_18.png)

![](img/9cfac7f54709a60a64f397cb3bb38731_19.png)

![](img/9cfac7f54709a60a64f397cb3bb38731_20.png)

// 设置静态文件中间件，public 目录下的文件可通过 HTTP 直接访问
app.use(express.static(‘public‘));

![](img/9cfac7f54709a60a64f397cb3bb38731_22.png)

// 服务器开始监听 3000 端口
server.listen(3000, () => {
    console.log(‘Server listening on port 3000‘);
});
```

![](img/9cfac7f54709a60a64f397cb3bb38731_24.png)

### 3.3 创建基础 HTML 页面

![](img/9cfac7f54709a60a64f397cb3bb38731_26.png)

为了让服务器有内容可提供，我们在 `public/index.html` 中创建一个简单的聊天界面。

![](img/9cfac7f54709a60a64f397cb3bb38731_28.png)

```html
<!DOCTYPE html>
<html lang=“en“>
<head>
    <meta charset=“UTF-8“>
    <title>Socket.IO Chat</title>
</head>
<body>
    <ul id=“chat“></ul> <!-- 用于显示聊天消息的列表 -->
    <form id=“form“ action=““>
        <input id=“input“ autocomplete=“off“ /> <!-- 消息输入框 -->
        <button type=“submit“>Send</button> <!-- 发送按钮 -->
    </form>
</body>
</html>
```

现在，运行 `npm start` 并访问 `http://localhost:3000`，你应该能看到一个简单的输入框和按钮。这证明我们的静态服务器工作正常。

![](img/9cfac7f54709a60a64f397cb3bb38731_30.png)

## 4. 集成 Socket.IO

基础服务器就绪后，本节我们将把 Socket.IO 集成到项目中，建立客户端与服务器之间的 WebSocket 连接。

![](img/9cfac7f54709a60a64f397cb3bb38731_32.png)

![](img/9cfac7f54709a60a64f397cb3bb38731_34.png)

### 4.1 安装 Socket.IO

![](img/9cfac7f54709a60a64f397cb3bb38731_36.png)

在项目根目录下运行以下命令来安装 Socket.IO 库：
```bash
npm install socket.io
```
这个命令会自动将 `socket.io` 依赖添加到 `package.json` 文件中。

### 4.2 设置服务器端 Socket.IO

![](img/9cfac7f54709a60a64f397cb3bb38731_38.png)

![](img/9cfac7f54709a60a64f397cb3bb38731_39.png)

![](img/9cfac7f54709a60a64f397cb3bb38731_41.png)

修改 `app.js`，引入 Socket.IO 并将其绑定到我们的 HTTP 服务器上。

```javascript
const express = require(‘express‘);
const http = require(‘http‘);
const socketIo = require(‘socket.io‘); // 导入 Socket.IO

![](img/9cfac7f54709a60a64f397cb3bb38731_43.png)

const app = express();
const server = http.createServer(app);
const io = socketIo(server); // 将 Socket.IO 绑定到 HTTP 服务器

![](img/9cfac7f54709a60a64f397cb3bb38731_45.png)

app.use(express.static(‘public‘));

![](img/9cfac7f54709a60a64f397cb3bb38731_47.png)

// 监听客户端连接事件
io.on(‘connection‘, (socket) => {
    console.log(‘A user connected‘);

    // 监听客户端断开连接事件
    socket.on(‘disconnect‘, () => {
        console.log(‘User disconnected‘);
    });
});

![](img/9cfac7f54709a60a64f397cb3bb38731_49.png)

![](img/9cfac7f54709a60a64f397cb3bb38731_50.png)

server.listen(3000, () => {
    console.log(‘Server listening on port 3000‘);
});
```
*   `io.on(‘connection‘, ...)`：当有客户端通过 WebSocket 连接到服务器时，触发此事件。回调函数中的 `socket` 对象代表与这个特定客户端的连接。
*   `socket.on(‘disconnect‘, ...)`：监听这个特定客户端的断开连接事件。

![](img/9cfac7f54709a60a64f397cb3bb38731_52.png)

### 4.3 设置客户端 Socket.IO

服务器端设置好后，客户端也需要加载 Socket.IO 的客户端库并建立连接。修改 `public/index.html`，在 `</body>` 标签前添加以下脚本。

![](img/9cfac7f54709a60a64f397cb3bb38731_54.png)

```html
    <!-- 由 Socket.IO 服务器自动提供的客户端库 -->
    <script src=“/socket.io/socket.io.js“></script>
    <!-- 我们自己的客户端逻辑 -->
    <script src=“/scripts/chat.js“></script>
</body>
```
注意：`/socket.io/socket.io.js` 这个路径是由 Socket.IO 服务器自动生成的，无需我们手动放置文件。

![](img/9cfac7f54709a60a64f397cb3bb38731_56.png)

现在，在 `public/scripts/chat.js` 中，我们初始化客户端 Socket 连接。
```javascript
// 建立与服务器的 Socket 连接
// 它会自动连接到提供当前页面的主机（localhost:3000）
const socket = io();
```

![](img/9cfac7f54709a60a64f397cb3bb38731_58.png)

### 4.4 测试连接

![](img/9cfac7f54709a60a64f397cb3bb38731_60.png)

1.  重启服务器：`npm start`。
2.  打开浏览器访问 `http://localhost:3000`。
3.  查看运行服务器的终端，你应该能看到 “A user connected” 的日志。
4.  刷新浏览器页面，终端会先显示 “User disconnected”，然后显示新的 “A user connected”。这表明连接和断开事件都被成功捕获。

![](img/9cfac7f54709a60a64f397cb3bb38731_62.png)

## 5. 实现聊天功能：发送与广播消息

![](img/9cfac7f54709a60a64f397cb3bb38731_64.png)

我们已经建立了双向连接，本节将实现聊天的核心功能：客户端发送消息，服务器接收并广播给所有客户端。

![](img/9cfac7f54709a60a64f397cb3bb38731_66.png)

![](img/9cfac7f54709a60a64f397cb3bb38731_67.png)

### 5.1 客户端：发送消息事件

![](img/9cfac7f54709a60a64f397cb3bb38731_69.png)

![](img/9cfac7f54709a60a64f397cb3bb38731_71.png)

首先，在客户端处理表单提交，将输入框中的消息发送给服务器。更新 `public/scripts/chat.js`：

```javascript
const socket = io();
// 获取 DOM 元素
const form = document.getElementById(‘form‘);
const input = document.getElementById(‘input‘);
const chat = document.getElementById(‘chat‘); // 消息列表容器

![](img/9cfac7f54709a60a64f397cb3bb38731_73.png)

// 监听表单提交事件
form.addEventListener(‘submit‘, (event) => {
    event.preventDefault(); // 阻止表单默认的 HTTP 提交行为

    if (input.value) {
        // 向服务器发射一个自定义事件 ‘chat-message‘，并携带消息内容
        socket.emit(‘chat-message‘, input.value);
        input.value = ‘‘; // 清空输入框
    }
});
```

### 5.2 服务器端：接收并广播消息

![](img/9cfac7f54709a60a64f397cb3bb38731_75.png)

![](img/9cfac7f54709a60a64f397cb3bb38731_77.png)

然后，在服务器端监听客户端发来的 `chat-message` 事件，并将消息广播给所有已连接的客户端。更新 `app.js` 中 `io.on(‘connection‘)` 内的代码：

![](img/9cfac7f54709a60a64f397cb3bb38731_79.png)

```javascript
io.on(‘connection‘, (socket) => {
    console.log(‘A user connected‘);

    // 监听客户端发来的 ‘chat-message‘ 事件
    socket.on(‘chat-message‘, (msg) => {
        console.log(‘Message:‘, msg); // 在服务器控制台打印消息
        // 将消息广播给所有客户端（包括发送者）
        io.emit(‘chat-message‘, msg);
    });

    socket.on(‘disconnect‘, () => {
        console.log(‘User disconnected‘);
    });
});
```
*   `socket.on(‘chat-message‘, ...)`：监听来自当前客户端的 `chat-message` 事件。
*   `io.emit(‘chat-message‘, msg)`：使用 `io`（服务器对象）向**所有**已连接的客户端发射 `chat-message` 事件。如果想排除发送者，可以使用 `socket.broadcast.emit(...)`。

### 5.3 客户端：接收并显示广播的消息

![](img/9cfac7f54709a60a64f397cb3bb38731_81.png)

最后，客户端需要监听服务器广播的 `chat-message` 事件，并将消息显示在页面上。在 `public/scripts/chat.js` 的末尾添加：

![](img/9cfac7f54709a60a64f397cb3bb38731_82.png)

![](img/9cfac7f54709a60a64f397cb3bb38731_83.png)

![](img/9cfac7f54709a60a64f397cb3bb38731_85.png)

![](img/9cfac7f54709a60a64f397cb3bb38731_86.png)

```javascript
// 监听服务器广播的 ‘chat-message‘ 事件
socket.on(‘chat-message‘, (msg) => {
    // 创建一个新的列表项元素来显示消息
    const item = document.createElement(‘li‘);
    item.textContent = msg;
    // 将消息添加到聊天列表中
    chat.appendChild(item);
    // 滚动到窗口底部，以便看到最新消息
    window.scrollTo(0, document.body.scrollHeight);
});
```

![](img/9cfac7f54709a60a64f397cb3bb38731_88.png)

### 5.4 测试聊天功能

1.  重启服务器。
2.  打开两个或多个浏览器标签页，均访问 `http://localhost:3000`。
3.  在其中一个标签页的输入框中输入消息并点击发送。
4.  观察所有打开的标签页，消息应该会实时出现在每个页面的聊天列表中。同时，服务器终端也会打印出发送的消息。

## 总结

![](img/9cfac7f54709a60a64f397cb3bb38731_90.png)

在本节课中，我们一起学习了 WebSocket 和 Socket.IO 的基础知识，并成功构建了一个简单的实时聊天应用。我们涵盖了以下关键步骤：

1.  **理解核心概念**：了解了 WebSocket 的全双工、持久连接特性，以及它与 HTTP 轮询的区别。
2.  **项目初始化**：设置了项目结构、`package.json` 和基础的 Express 静态服务器。
3.  **集成 Socket.IO**：在服务器端和客户端安装了 Socket.IO 并建立了 WebSocket 连接。
4.  **实现事件通信**：
    *   客户端使用 `socket.emit()` 向服务器发送自定义事件（`chat-message`）。
    *   服务器使用 `socket.on()` 监听来自客户端的事件。
    *   服务器使用 `io.emit()` 将接收到的消息广播给所有客户端。
    *   客户端使用 `socket.on()` 监听服务器广播的事件，并更新用户界面。

![](img/9cfac7f54709a60a64f397cb3bb38731_92.png)

![](img/9cfac7f54709a60a64f397cb3bb38731_94.png)

你现在已经掌握了使用 Socket.IO 进行实时双向通信的基本模式。你可以在此基础上扩展功能，例如添加用户昵称、私聊、房间系统、消息持久化存储或更复杂的实时交互应用（如协作白板、简单多人在线游戏等）。