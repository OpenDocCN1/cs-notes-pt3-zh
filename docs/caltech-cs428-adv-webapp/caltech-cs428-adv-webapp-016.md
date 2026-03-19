# 016：REST API 第一部分

![](img/b751a18fb4fe1305e878c78006301e72_0.png)

## 概述

在本节课中，我们将学习如何使用 Express 框架设计和实现一个 REST API。我们将构建一个多人版的“猜数字”游戏服务器，客户端可以通过发送 HTTP 请求来参与游戏。通过本教程，你将掌握路由参数、查询字符串、唯一标识符（UID）以及如何组织后端代码。

---

## 1. 课程介绍与核心概念

上一节我们介绍了后端技术的基础。本节中，我们将深入探讨 REST API 的设计与实现。

REST API 是一种通过网络（通常是 HTTP 协议）提供数据访问的 Web 服务接口。它可以为其他后端服务或前端应用提供数据。

### 核心概念

*   **API (应用程序接口)**: 一组预定义的函数或方法集合，开发者可以调用它们。
*   **REST API (表述性状态转移接口)**: 指使用 HTTP 协议来提供 API 访问的方式。其核心是**通过标准的 HTTP 方法（GET, POST, PUT, DELETE 等）对资源进行操作**。
*   **端点 (Endpoint)**: API 与远程系统交互的接触点。对我们而言，端点就是服务器的 URL，用于请求或发送数据。
*   **Express**: 一个基于 Node.js 的 Web 应用框架，用于快速搭建服务器和处理 HTTP 请求。
*   **路由参数 (Route Parameters)**: 允许我们在 URL 中定义变量部分。例如，`/game/:id` 中的 `:id` 可以匹配任何值。
*   **查询字符串 (Query String)**: 附加在 URL 问号（?）后面的键值对，用于向服务器传递数据。格式为 `?key1=value1&key2=value2`。
*   **唯一标识符 (UID)**: 用于唯一标识某个资源（如一个游戏会话）。我们将使用 `shortid` 模块来生成易于分享的短 ID。

---

## 2. REST API 设计

在开始编码之前，我们需要设计 API 的端点和功能。这有助于我们清晰地规划代码结构。

以下是我们的“猜数字”游戏 API 设计表：

| HTTP 方法 | 端点 (路由) | 描述 | 请求参数 (查询字符串) | 服务器行为 |
| :--- | :--- | :--- | :--- | :--- |
| **GET** | `/api/game/new` | 创建新游戏 | `start`: 范围起始值 <br> `end`: 范围结束值 | 在指定范围内生成一个随机密码，创建一个新游戏实例，并返回其唯一 ID。 |
| **GET** | `/api/game/:id` | 获取游戏信息 | 无 | 根据提供的 `:id` 返回对应游戏的状态（如范围、是否结束），但不返回密码。 |
| **GET** | `/api/game/:id/guess` | 提交猜测 | `guess`: 猜测的数字 | 在 ID 对应的游戏中检查猜测。返回结果：`correct`（正确）、`too low`（太低）、`too high`（太高）、`game over`（游戏已结束）或 `error`（错误）。 |
| **GET** | `/api/game/:id/reset` | 重置游戏 | 无 | 如果游戏已结束，则重置游戏：生成新密码并将游戏状态设为未结束。 |

---

## 3. 项目初始化与配置

现在，我们开始构建项目。首先，我们需要设置项目的基本结构和配置文件。

### 步骤 1: 创建项目结构

在终端中执行以下命令，创建项目目录和必要的文件：

```bash
mkdir highlow-server
cd highlow-server
touch package.json app.js
mkdir routes controllers models
```

### 步骤 2: 配置 package.json

`package.json` 文件用于管理项目的元数据、依赖和脚本。

打开 `package.json` 文件，并输入以下内容：

```json
{
  "name": "highlow-rest-api",
  "version": "1.0.0",
  "description": "A backend API for a high-low number guessing game.",
  "main": "app.js",
  "scripts": {
    "start": "node app.js"
  },
  "dependencies": {
    "express": "*",
    "shortid": "*"
  }
}
```

**代码解释**:
*   `name`, `version`, `description`: 项目的基本信息。
*   `main`: 应用的入口文件。
*   `scripts`: 定义可以通过 `npm run <script-name>` 运行的命令。`npm start` 会直接运行 `node app.js`。
*   `dependencies`: 项目依赖的模块。`*` 表示使用最新版本。

### 步骤 3: 安装依赖

在项目根目录下运行以下命令，安装 `express` 和 `shortid` 模块：

```bash
npm install
```

![](img/b751a18fb4fe1305e878c78006301e72_2.png)

此命令会创建 `node_modules` 文件夹和 `package-lock.json` 文件。

![](img/b751a18fb4fe1305e878c78006301e72_4.png)

![](img/b751a18fb4fe1305e878c78006301e72_6.png)

---

## 4. 搭建基础 Express 应用

接下来，我们创建应用的主文件并启动一个基本的服务器。

![](img/b751a18fb4fe1305e878c78006301e72_8.png)

![](img/b751a18fb4fe1305e878c78006301e72_10.png)

打开 `app.js` 文件，输入以下代码：

```javascript
// 1. 导入所需模块
const express = require('express');
const path = require('path');
const bodyParser = require('body-parser');

![](img/b751a18fb4fe1305e878c78006301e72_12.png)

// 2. 创建 Express 应用实例
const app = express();

// 3. 定义端口（优先使用环境变量，便于部署）
const PORT = process.env.PORT || 3000;

// 4. 设置中间件
// 解析 application/json 格式的请求体
app.use(bodyParser.json());
// 解析 application/x-www-form-urlencoded 格式的请求体（用于查询字符串）
app.use(bodyParser.urlencoded({ extended: true }));

![](img/b751a18fb4fe1305e878c78006301e72_14.png)

// 5. 启动服务器，监听指定端口
app.listen(PORT, () => {
  console.log(`Server is running on port ${PORT}`);
});
```

**代码解释**:
*   我们导入了 `express`, `path`, `body-parser` 模块。
*   `body-parser` 中间件用于解析客户端发送的请求数据。
*   `app.listen()` 启动服务器并在指定端口监听请求。

![](img/b751a18fb4fe1305e878c78006301e72_16.png)

![](img/b751a18fb4fe1305e878c78006301e72_18.png)

现在，你可以运行 `npm start` 来启动服务器。如果看到 `Server is running on port 3000` 的输出，说明服务器已成功启动。

![](img/b751a18fb4fe1305e878c78006301e72_20.png)

---

![](img/b751a18fb4fe1305e878c78006301e72_22.png)

## 5. 创建测试路由与控制器

![](img/b751a18fb4fe1305e878c78006301e72_24.png)

![](img/b751a18fb4fe1305e878c78006301e72_26.png)

![](img/b751a18fb4fe1305e878c78006301e72_28.png)

为了验证我们的服务器能正常工作，我们先创建一个简单的测试端点。

![](img/b751a18fb4fe1305e878c78006301e72_30.png)

![](img/b751a18fb4fe1305e878c78006301e72_32.png)

![](img/b751a18fb4fe1305e878c78006301e72_34.png)

我们将遵循 MVC（模型-视图-控制器）模式来组织代码：
*   **模型 (Models)**: 管理数据（游戏状态、逻辑）。
*   **视图 (Views)**: 本 API 不涉及前端视图。
*   **控制器 (Controllers)**: 处理请求，调用模型，并发送响应。
*   **路由 (Routes)**: 定义 URL 端点与控制器方法的映射关系。

### 步骤 1: 创建控制器

在 `controllers/` 目录下创建 `game.controller.js` 文件：

```javascript
// 控制器类，包含处理请求的方法
class GameController {
  // 测试方法，返回一个简单的 JSON 响应
  test(req, res) {
    res.json({ success: true });
  }
}

![](img/b751a18fb4fe1305e878c78006301e72_36.png)

// 导出控制器的一个实例
module.exports = new GameController();
```

### 步骤 2: 创建路由

在 `routes/` 目录下创建 `game.routes.js` 文件：

![](img/b751a18fb4fe1305e878c78006301e72_38.png)

```javascript
// 1. 导入 Express 的路由功能
const express = require('express');
const router = express.Router();

![](img/b751a18fb4fe1305e878c78006301e72_40.png)

// 2. 从控制器导入处理方法（这里使用解构赋值只导入 test 方法）
const { test } = require('../controllers/game.controller');

// 3. 定义路由：当收到对 `/test` 的 GET 请求时，调用控制器的 test 方法
router.get('/test', test);

// 4. 导出配置好的路由器
module.exports = router;
```

### 步骤 3: 在主应用中集成路由

修改 `app.js` 文件，在启动服务器之前添加路由：

![](img/b751a18fb4fe1305e878c78006301e72_42.png)

![](img/b751a18fb4fe1305e878c78006301e72_44.png)

```javascript
// ... 之前的导入和中间件设置代码 ...

// 导入游戏路由
const gameRoutes = require('./routes/game.routes');

// 将游戏路由挂载到 `/api/game` 路径下
// 这意味着所有 `/api/game/*` 的请求都将由 gameRoutes 处理
app.use('/api/game', gameRoutes);

![](img/b751a18fb4fe1305e878c78006301e72_46.png)

// ... 启动服务器的代码 ...
```

### 步骤 4: 测试

1.  重启服务器 (`npm start`)。
2.  在浏览器中访问 `http://localhost:3000/api/game/test`。
3.  你应该看到返回的 JSON 数据：`{"success": true}`。

这证明我们的路由和控制器已正确连接。

---

## 6. 实现游戏模型与创建游戏端点

现在，我们开始实现游戏的核心逻辑。

### 步骤 1: 创建游戏模型

在 `models/` 目录下创建 `game.model.js` 文件：

![](img/b751a18fb4fe1305e878c78006301e72_48.png)

```javascript
// 导入 shortid 模块，用于生成唯一、易读的 ID
const shortid = require('shortid');

// 游戏服务器类，管理所有游戏实例
class GameServer {
  constructor() {
    // 用一个对象来存储所有游戏，键是游戏ID，值是游戏数据
    this.games = {};
  }

  // 创建新游戏的方法
  create(start, end) {
    // 1. 在 start 和 end 范围内生成随机密码
    const number = Math.floor(Math.random() * (end - start + 1)) + start;

    // 2. 生成唯一游戏 ID
    const id = shortid.generate();

    // 3. 创建游戏对象
    const game = {
      number,     // 密码（不发送给客户端）
      start,      // 范围起始
      end,        // 范围结束
      gameOver: false, // 游戏是否结束
      id          // 游戏 ID
    };

    // 4. 将游戏存入集合
    this.games[id] = game;

    // 5. 返回游戏 ID 给调用者
    return id;
  }
}

// 导出 GameServer 的一个实例（单例模式）
module.exports = new GameServer();
```

### 步骤 2: 在控制器中添加创建游戏的方法

修改 `controllers/game.controller.js` 文件：

```javascript
// 导入游戏模型
const gameModel = require('../models/game.model');

class GameController {
  test(req, res) { /* ... 保持不变 ... */ }

  // 创建新游戏的方法
  newGame(req, res) {
    // 从查询字符串中获取 start 和 end 参数
    const { start, end } = req.query;

    // 调用模型创建游戏，并获取游戏 ID
    const gameId = gameModel.create(parseInt(start), parseInt(end));

    // 返回成功响应和游戏 ID
    res.json({
      success: true,
      gameId: gameId
    });
  }
}

![](img/b751a18fb4fe1305e878c78006301e72_50.png)

![](img/b751a18fb4fe1305e878c78006301e72_52.png)

![](img/b751a18fb4fe1305e878c78006301e72_54.png)

module.exports = new GameController();
```

![](img/b751a18fb4fe1305e878c78006301e72_56.png)

### 步骤 3: 在路由中注册新端点

![](img/b751a18fb4fe1305e878c78006301e72_58.png)

修改 `routes/game.routes.js` 文件：

![](img/b751a18fb4fe1305e878c78006301e72_59.png)

```javascript
const express = require('express');
const router = express.Router();
// 从控制器导入 newGame 方法
const { test, newGame } = require('../controllers/game.controller');

router.get('/test', test);
// 注册创建游戏的路由
router.get('/new', newGame);

![](img/b751a18fb4fe1305e878c78006301e72_61.png)

module.exports = router;
```

![](img/b751a18fb4fe1305e878c78006301e72_63.png)

### 步骤 4: 测试创建游戏

![](img/b751a18fb4fe1305e878c78006301e72_65.png)

![](img/b751a18fb4fe1305e878c78006301e72_67.png)

1.  重启服务器。
2.  在浏览器中访问：`http://localhost:3000/api/game/new?start=0&end=100`
3.  你应该会收到一个包含 `gameId` 的 JSON 响应，例如：`{"success":true,"gameId":"abc123"}`。
4.  查看服务器终端，应该会打印出刚创建的游戏数据。

![](img/b751a18fb4fe1305e878c78006301e72_69.png)

![](img/b751a18fb4fe1305e878c78006301e72_71.png)

---

![](img/b751a18fb4fe1305e878c78006301e72_73.png)

![](img/b751a18fb4fe1305e878c78006301e72_75.png)

## 7. 实现获取游戏信息端点

现在，我们需要实现一个端点，让客户端能根据游戏 ID 获取游戏状态（不包含密码）。

### 步骤 1: 在模型中添加获取游戏的方法

修改 `models/game.model.js` 文件，在 `GameServer` 类中添加：

![](img/b751a18fb4fe1305e878c78006301e72_77.png)

```javascript
get(id) {
  // 检查游戏 ID 是否存在
  if (this.games[id]) {
    const game = this.games[id];
    // 使用解构赋值，将密码（number）分离出来，不返回给客户端
    const { number, ...publicData } = game;
    return publicData; // 返回不包含密码的游戏数据
  } else {
    return null; // 游戏不存在
  }
}
```

### 步骤 2: 在控制器中添加获取游戏的方法

修改 `controllers/game.controller.js` 文件，在 `GameController` 类中添加：

```javascript
getGame(req, res) {
  // 从路由参数中获取游戏 ID
  const { id } = req.params;

  // 调用模型获取游戏数据
  const gameData = gameModel.get(id);

  if (gameData) {
    // 游戏存在，返回数据并标记成功
    gameData.success = true;
    res.json(gameData);
  } else {
    // 游戏不存在，返回失败
    res.json({ success: false });
  }
}
```

### 步骤 3: 在路由中注册新端点（使用路由参数）

修改 `routes/game.routes.js` 文件：

```javascript
const { test, newGame, getGame } = require('../controllers/game.controller');

router.get('/test', test);
router.get('/new', newGame);
// 定义带参数的路由。:id 是一个占位符，可以匹配任何值
// 注意：具体的路由（如 /test, /new）要放在参数路由前面
router.get('/:id', getGame);
```

### 步骤 4: 测试获取游戏

1.  重启服务器。
2.  首先创建一个新游戏，获取其 `gameId`（例如 `abc123`）。
3.  在浏览器中访问：`http://localhost:3000/api/game/abc123`
4.  你应该会收到类似 `{"start":"0","end":"100","gameOver":false,"id":"abc123","success":true}` 的响应。注意，其中没有 `number` 字段。
5.  尝试访问一个不存在的 ID，应该会收到 `{"success":false}`。

---

## 8. 实现提交猜测端点

这是游戏的核心交互端点。

### 步骤 1: 在模型中添加猜测逻辑

![](img/b751a18fb4fe1305e878c78006301e72_79.png)

修改 `models/game.model.js` 文件，在 `GameServer` 类中添加：

![](img/b751a18fb4fe1305e878c78006301e72_81.png)

```javascript
guess(id, guessNumber) {
  const game = this.games[id];
  if (!game) {
    return null; // 游戏不存在
  }

  if (game.gameOver) {
    return { guess: 'game over' }; // 游戏已结束
  }

  // 将猜测值和密码转换为数字进行比较
  const guessNum = parseInt(guessNumber);
  const secretNum = parseInt(game.number);

  if (guessNum === secretNum) {
    game.gameOver = true; // 猜对了，游戏结束
    return { guess: 'correct' };
  } else if (guessNum < secretNum) {
    return { guess: 'too low' };
  } else if (guessNum > secretNum) {
    return { guess: 'too high' };
  } else {
    return { guess: 'error' }; // 例如，guessNumber 不是数字
  }
}
```

### 步骤 2: 在控制器中添加处理猜测的方法

修改 `controllers/game.controller.js` 文件，在 `GameController` 类中添加：

```javascript
makeGuess(req, res) {
  // id 来自路由参数
  const { id } = req.params;
  // guess 来自查询字符串
  const { guess } = req.query;

  // 调用模型进行猜测
  const result = gameModel.guess(id, guess);

  if (result) {
    // 模型返回了结果（无论对错）
    result.success = true;
    res.json(result);
  } else {
    // 模型返回 null，说明游戏 ID 无效
    res.json({ success: false });
  }
}
```

### 步骤 3: 在路由中注册猜测端点

修改 `routes/game.routes.js` 文件：

```javascript
const { test, newGame, getGame, makeGuess } = require('../controllers/game.controller');

// ... 其他路由 ...

// 定义嵌套路由：/api/game/:id/guess
router.get('/:id/guess', makeGuess);
```

### 步骤 4: 测试猜测功能

1.  重启服务器并创建一个新游戏，获取 `gameId`。
2.  在浏览器中进行猜测，例如：`http://localhost:3000/api/game/abc123/guess?guess=50`
3.  根据随机生成的密码，你会收到 `{"guess":"too low","success":true}` 或 `{"guess":"too high","success":true}` 等响应。
4.  不断尝试，直到猜中，你会收到 `{"guess":"correct","success":true}`。此时游戏状态变为结束。
5.  游戏结束后再次猜测，会收到 `{"guess":"game over","success":true}`。
6.  测试无效的 ID 或非数字猜测。

---

## 9. 实现重置游戏端点

最后，我们实现一个端点，允许在游戏结束后重置游戏，以便重新开始。

### 步骤 1: 在模型中添加重置方法

修改 `models/game.model.js` 文件，在 `GameServer` 类中添加：

```javascript
reset(id) {
  const game = this.games[id];
  // 只有游戏存在且已结束时才能重置
  if (game && game.gameOver) {
    // 生成新的随机密码
    game.number = Math.floor(Math.random() * (game.end - game.start + 1)) + game.start;
    game.gameOver = false; // 重置游戏状态

    // 返回公开的游戏数据（不包含新密码）
    const { number, ...publicData } = game;
    return publicData;
  }
  return null; // 无法重置
}
```

### 步骤 2: 在控制器中添加重置方法

修改 `controllers/game.controller.js` 文件，在 `GameController` 类中添加：

```javascript
resetGame(req, res) {
  const { id } = req.params;
  const result = gameModel.reset(id);

  if (result) {
    result.success = true;
    res.json(result);
  } else {
    res.json({ success: false });
  }
}
```

### 步骤 3: 在路由中注册重置端点

修改 `routes/game.routes.js` 文件：

![](img/b751a18fb4fe1305e878c78006301e72_83.png)

![](img/b751a18fb4fe1305e878c78006301e72_85.png)

![](img/b751a18fb4fe1305e878c78006301e72_87.png)

```javascript
const { test, newGame, getGame, makeGuess, resetGame } = require('../controllers/game.controller');

// ... 其他路由 ...

![](img/b751a18fb4fe1305e878c78006301e72_89.png)

![](img/b751a18fb4fe1305e878c78006301e72_90.png)

router.get('/:id/reset', resetGame);
```

![](img/b751a18fb4fe1305e878c78006301e72_92.png)

### 步骤 4: 测试重置功能

![](img/b751a18fb4fe1305e878c78006301e72_94.png)

1.  重启服务器。
2.  创建一个游戏并猜中它（使其状态为 `game over`）。
3.  访问重置端点：`http://localhost:3000/api/game/abc123/reset`
4.  你应该收到成功响应，并且 `gameOver` 字段变回 `false`。
5.  再次获取游戏信息或进行猜测，验证游戏已重置。
6.  尝试重置一个未结束的游戏或无效 ID，应返回 `{"success":false}`。

![](img/b751a18fb4fe1305e878c78006301e72_96.png)

![](img/b751a18fb4fe1305e878c78006301e72_98.png)

---

![](img/b751a18fb4fe1305e878c78006301e72_99.png)

![](img/b751a18fb4fe1305e878c78006301e72_101.png)

## 10. 处理跨域资源共享 (CORS)

为了在下一节课中能够从另一个本地前端应用访问这个 API，我们需要在服务器端设置 CORS 头，允许跨域请求。

修改 `app.js` 文件，在设置路由之前添加一个自定义中间件：

```javascript
// ... 导入模块和基础设置 ...

// 自定义中间件：设置 CORS 头部，允许来自任何源的请求（仅用于开发）
app.use((req, res, next) => {
  res.header('Access-Control-Allow-Origin', '*'); // 允许任何源
  res.header('Access-Control-Allow-Headers', 'Origin, X-Requested-With, Content-Type, Accept');
  next(); // 继续处理请求
});

// ... 导入路由和启动服务器 ...
```

**注意**：在生产环境中，应将 `*` 替换为具体的前端域名以提高安全性。

---

## 总结

![](img/b751a18fb4fe1305e878c78006301e72_103.png)

![](img/b751a18fb4fe1305e878c78006301e72_104.png)

在本节课中，我们一起学习了如何设计和实现一个完整的 REST API：

1.  **理解了核心概念**：REST API、端点、路由参数、查询字符串和 UID。
2.  **设计了 API 规范**：通过表格规划了各个端点的功能、方法和参数。
3.  **搭建了项目结构**：使用 `package.json` 管理依赖，并组织了 `models`、`controllers`、`routes` 目录。
4.  **实现了游戏模型**：使用 `GameServer` 类管理所有游戏实例的状态和核心逻辑（创建、获取、猜测、重置）。
5.  **创建了控制器**：编写了处理不同 HTTP 请求的方法，作为模型和路由之间的桥梁。
6.  **配置了路由**：使用 Express Router 将 URL 映射到对应的控制器方法，并学会了使用路由参数（`:id`）。
7.  **处理了数据交互**：通过 `req.params` 获取路由参数，通过 `req.query` 获取查询字符串。
8.  **设置了 CORS**：为后续的前后端分离开发做好了准备。

你现在已经拥有了一个功能完整的多人“猜数字”游戏后端 API。在下一节课中，我们将构建一个前端客户端来使用这个 API，实现一个真正的可交互游戏。

![](img/b751a18fb4fe1305e878c78006301e72_106.png)

**扩展思考**：
*   如何为游戏添加玩家用户名和积分榜？
*   如何将游戏数据持久化到数据库中，防止服务器重启后数据丢失？
*   如何将这个 API 部署到云服务器（如 Heroku）上，让其他人也能访问？