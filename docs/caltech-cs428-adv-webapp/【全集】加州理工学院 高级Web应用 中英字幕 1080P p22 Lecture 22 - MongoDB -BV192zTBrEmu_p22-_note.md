# 高级Web应用：第22讲：MongoDB CRUD + JWT 教程 🚀

![](img/6c68f1f2b6558d155ff370ad0b7cb864_0.png)

在本教程中，我们将学习如何构建一个简单的全栈应用。我们将部署一个本地的MongoDB数据库服务器，并使用Express应用作为客户端连接到它。然后，我们将实现CRUD（创建、读取、更新、删除）操作，并集成JSON Web Token（JWT）进行身份验证。通过本教程，你将了解客户端、服务器和数据库之间如何通信，为你的最终项目打下基础。

## 概述 📋

我们将分三个阶段进行：
1.  **基础设置**：启动MongoDB服务器和Express Web服务器。
2.  **连接与CRUD**：使用Mongoose连接Express应用到MongoDB，并实现所有CRUD操作。
3.  **JWT身份验证**：实现基于JWT的登录和受保护路由。

---

## 第一部分：基础设置

### 1.1 启动MongoDB服务器 🗄️

首先，你需要在本地机器上安装并运行MongoDB服务器（`mongod`）。

**步骤：**
1.  从MongoDB官网下载并安装MongoDB社区版。
2.  在项目根目录下创建一个名为 `data` 的文件夹，用于存储数据库文件。
3.  打开终端，导航到项目根目录，运行以下命令启动MongoDB服务器：

```bash
mongod --dbpath ./data --port 27017 --bind_ip 127.0.0.1
```

**验证：**
如果服务器成功启动，终端将持续输出日志信息。同时，`data` 文件夹中会生成MongoDB所需的文件。

### 1.2 配置Express服务器 🌐

接下来，我们将设置一个基本的Express服务器来提供静态文件。

**步骤：**
1.  在项目根目录初始化Node.js项目并安装Express。
2.  创建 `app.js` 文件作为服务器入口。
3.  创建 `public` 文件夹存放前端文件（HTML, CSS, JS）。

**`app.js` 基础代码：**

```javascript
const express = require('express');
const app = express();
const port = 3000;

// 提供静态文件
app.use(express.static('public'));

![](img/6c68f1f2b6558d155ff370ad0b7cb864_2.png)

// 根路由，返回首页
app.get('/', (req, res) => {
    res.sendFile(__dirname + '/public/index.html');
});

// 启动服务器
app.listen(port, () => {
    console.log(`Server running on port ${port}`);
});
```

![](img/6c68f1f2b6558d155ff370ad0b7cb864_4.png)

**验证：**
运行 `npm start` 后，访问 `http://localhost:3000`，应能看到你的 `index.html` 页面。

---

![](img/6c68f1f2b6558d155ff370ad0b7cb864_6.png)

## 第二部分：连接数据库与CRUD操作

![](img/6c68f1f2b6558d155ff370ad0b7cb864_8.png)

![](img/6c68f1f2b6558d155ff370ad0b7cb864_10.png)

![](img/6c68f1f2b6558d155ff370ad0b7cb864_12.png)

上一节我们成功运行了Web服务器和数据库服务器。本节中，我们将使用Mongoose库连接两者，并开始操作数据。

![](img/6c68f1f2b6558d155ff370ad0b7cb864_14.png)

### 2.1 连接MongoDB 🔗

我们将使用Mongoose，它是一个基于MongoDB原生驱动的ODM（对象文档映射）库，支持模式（Schema）定义。

![](img/6c68f1f2b6558d155ff370ad0b7cb864_16.png)

![](img/6c68f1f2b6558d155ff370ad0b7cb864_18.png)

**步骤：**
1.  安装Mongoose：`npm install mongoose`
2.  创建配置文件 `config/database.js`，存放数据库连接URL。
3.  在 `app.js` 中导入配置并使用Mongoose连接数据库。

![](img/6c68f1f2b6558d155ff370ad0b7cb864_20.png)

**`config/database.js`：**

![](img/6c68f1f2b6558d155ff370ad0b7cb864_22.png)

```javascript
module.exports = {
    database: 'mongodb://127.0.0.1:27017/my_app_data'
};
```

![](img/6c68f1f2b6558d155ff370ad0b7cb864_24.png)

**在 `app.js` 中添加连接代码：**

![](img/6c68f1f2b6558d155ff370ad0b7cb864_26.png)

![](img/6c68f1f2b6558d155ff370ad0b7cb864_28.png)

```javascript
const mongoose = require('mongoose');
const { database } = require('./config/database');

![](img/6c68f1f2b6558d155ff370ad0b7cb864_30.png)

// 连接MongoDB
mongoose.connect(database, {
    useNewUrlParser: true,
    useUnifiedTopology: true
}).then(() => {
    console.log('Database Connected');
}).catch(err => {
    console.log('Connection Error: ' + err);
});
```

![](img/6c68f1f2b6558d155ff370ad0b7cb864_32.png)

### 2.2 定义数据模型（Schema）📝

![](img/6c68f1f2b6558d155ff370ad0b7cb864_34.png)

在操作数据之前，我们需要定义数据的结构。我们将创建一个 `User` 模型。

**步骤：**
1.  创建 `models/User.js` 文件。
2.  使用Mongoose的Schema定义用户字段。

![](img/6c68f1f2b6558d155ff370ad0b7cb864_36.png)

**`models/User.js`：**

```javascript
const mongoose = require('mongoose');
const Schema = mongoose.Schema;

![](img/6c68f1f2b6558d155ff370ad0b7cb864_38.png)

![](img/6c68f1f2b6558d155ff370ad0b7cb864_40.png)

// 定义用户模式
const userSchema = new Schema({
    email: String,
    password: String
});

![](img/6c68f1f2b6558d155ff370ad0b7cb864_42.png)

// 创建并导出模型
module.exports = mongoose.model('User', userSchema);
```

### 2.3 实现CRUD端点 🛠️

![](img/6c68f1f2b6558d155ff370ad0b7cb864_44.png)

![](img/6c68f1f2b6558d155ff370ad0b7cb864_46.png)

我们将创建API路由来处理对用户数据的各种操作。以下是核心操作及其对应的HTTP方法：
*   **C (Create)** -> `POST`
*   **R (Read All)** -> `GET`
*   **R (Read One)** -> `GET` (带ID参数)
*   **U (Update)** -> `PUT`
*   **D (Delete)** -> `DELETE`

我们将路由逻辑组织在 `api/user-routes.js` 中。

**首先，安装并配置body-parser以解析请求体：**
`npm install body-parser`

![](img/6c68f1f2b6558d155ff370ad0b7cb864_48.png)

![](img/6c68f1f2b6558d155ff370ad0b7cb864_50.png)

**在 `app.js` 中启用：**

![](img/6c68f1f2b6558d155ff370ad0b7cb864_52.png)

![](img/6c68f1f2b6558d155ff370ad0b7cb864_54.png)

```javascript
const bodyParser = require('body-parser');
const userRoutes = require('./api/user-routes');

![](img/6c68f1f2b6558d155ff370ad0b7cb864_56.png)

![](img/6c68f1f2b6558d155ff370ad0b7cb864_58.png)

app.use(bodyParser.json()); // 解析JSON格式的请求体
app.use('/', userRoutes); // 使用用户路由
```

![](img/6c68f1f2b6558d155ff370ad0b7cb864_60.png)

![](img/6c68f1f2b6558d155ff370ad0b7cb864_62.png)

#### 创建 (Create) - `POST /register`

**`api/user-routes.js` 中的实现：**

![](img/6c68f1f2b6558d155ff370ad0b7cb864_64.png)

```javascript
const express = require('express');
const router = express.Router();
const User = require('../models/User');

// 创建用户
router.post('/register', async (req, res) => {
    const { email, password } = req.body;
    const newUser = new User({ email, password });
    const savedUser = await newUser.save();
    res.json({
        status: true,
        message: 'Inserted',
        data: savedUser
    });
});

![](img/6c68f1f2b6558d155ff370ad0b7cb864_66.png)

module.exports = router;
```

**前端测试 (`public/scripts/api-tester.js`)：**

![](img/6c68f1f2b6558d155ff370ad0b7cb864_68.png)

![](img/6c68f1f2b6558d155ff370ad0b7cb864_70.png)

![](img/6c68f1f2b6558d155ff370ad0b7cb864_72.png)

![](img/6c68f1f2b6558d155ff370ad0b7cb864_74.png)

```javascript
async function testCreate() {
    const config = {
        method: 'POST',
        headers: {
            'Accept': 'application/json',
            'Content-Type': 'application/json'
        },
        body: JSON.stringify({
            email: document.getElementById('create-email').value,
            password: document.getElementById('create-password').value
        })
    };
    const response = await fetch('/register', config);
    const data = await response.json();
    document.body.innerHTML += `<p>${JSON.stringify(data)}</p>`;
}
```

#### 读取所有 (Read All) - `GET /users`

![](img/6c68f1f2b6558d155ff370ad0b7cb864_76.png)

**`api/user-routes.js` 中的实现：**

![](img/6c68f1f2b6558d155ff370ad0b7cb864_78.png)

```javascript
router.get('/users', async (req, res) => {
    const users = await User.find();
    res.status(200).json({
        message: 'Users fetched',
        data: users
    });
});
```

#### 读取单个 (Read One) - `GET /user/:id`

![](img/6c68f1f2b6558d155ff370ad0b7cb864_80.png)

**`api/user-routes.js` 中的实现：**

![](img/6c68f1f2b6558d155ff370ad0b7cb864_82.png)

![](img/6c68f1f2b6558d155ff370ad0b7cb864_84.png)

![](img/6c68f1f2b6558d155ff370ad0b7cb864_86.png)

```javascript
router.get('/user/:id', async (req, res) => {
    const user = await User.findById(req.params.id);
    if (user) {
        res.status(200).json(user);
    } else {
        res.status(404).json({ message: 'Data not found' });
    }
});
```

![](img/6c68f1f2b6558d155ff370ad0b7cb864_88.png)

#### 更新 (Update) - `PUT /update/:id`

**`api/user-routes.js` 中的实现：**

![](img/6c68f1f2b6558d155ff370ad0b7cb864_90.png)

```javascript
router.put('/update/:id', async (req, res) => {
    const updatedUser = await User.findOneAndUpdate(
        { _id: req.params.id },
        { $set: { email: req.body.email, password: req.body.password } },
        { new: true }
    );
    if (updatedUser) {
        res.status(200).json(updatedUser);
    } else {
        res.status(404).json({ message: 'Data not found' });
    }
});
```

#### 删除 (Delete) - `DELETE /delete/:id`

![](img/6c68f1f2b6558d155ff370ad0b7cb864_92.png)

**`api/user-routes.js` 中的实现：**

![](img/6c68f1f2b6558d155ff370ad0b7cb864_94.png)

```javascript
router.delete('/delete/:id', async (req, res) => {
    const result = await User.deleteOne({ _id: req.params.id });
    res.status(200).json({
        message: 'User data deleted',
        data: result
    });
});
```

**提示：** 在实际应用中，请为所有数据库操作添加 `try...catch` 块以进行错误处理，防止服务器因客户端错误请求而崩溃。

![](img/6c68f1f2b6558d155ff370ad0b7cb864_96.png)

![](img/6c68f1f2b6558d155ff370ad0b7cb864_98.png)

---

## 第三部分：JWT身份验证

![](img/6c68f1f2b6558d155ff370ad0b7cb864_100.png)

![](img/6c68f1f2b6558d155ff370ad0b7cb864_102.png)

上一节我们完成了数据的增删改查。本节我们将引入一种无状态的身份验证机制——JSON Web Token（JWT）。

### 3.1 JWT概念 🔐

![](img/6c68f1f2b6558d155ff370ad0b7cb864_104.png)

![](img/6c68f1f2b6558d155ff370ad0b7cb864_106.png)

![](img/6c68f1f2b6558d155ff370ad0b7cb864_108.png)

JWT是一种令牌，包含三部分：
1.  **Header**：标识生成签名所用的算法。
2.  **Payload**：包含声明（如用户ID）。
3.  **Signature**：由编码后的Header、Payload和密钥通过加密算法生成。

与基于Session的认证不同，JWT将认证状态存储在客户端令牌中，服务器无需保存会话列表，因此更具可扩展性。但需注意，令牌一旦泄露，他人即可冒充用户，因此必须妥善处理（如设置短期有效期）。

### 3.2 实现登录并签发JWT 🎫

![](img/6c68f1f2b6558d155ff370ad0b7cb864_110.png)

**步骤：**
1.  安装JWT库：`npm install jsonwebtoken`
2.  创建登录端点，验证用户凭证后签发令牌。

![](img/6c68f1f2b6558d155ff370ad0b7cb864_112.png)

![](img/6c68f1f2b6558d155ff370ad0b7cb864_114.png)

**`api/user-routes.js` 中的登录实现：**

```javascript
const jwt = require('jsonwebtoken');

![](img/6c68f1f2b6558d155ff370ad0b7cb864_116.png)

router.post('/login', async (req, res) => {
    const { email, password } = req.body;
    const user = await User.findOne({ email });

    if (!user) return res.status(401).json({ message: 'Invalid email' });
    if (user.password !== password) return res.status(401).json({ message: 'Invalid password' });

    // 创建JWT载荷
    const payload = { subject: user._id };
    const token = jwt.sign(payload, 'secret_key'); // 生产环境应使用环境变量存储密钥
    res.status(200).json({ token });
});
```

![](img/6c68f1f2b6558d155ff370ad0b7cb864_118.png)

![](img/6c68f1f2b6558d155ff370ad0b7cb864_120.png)

![](img/6c68f1f2b6558d155ff370ad0b7cb864_122.png)

**前端登录测试：**

```javascript
async function testLogin() {
    const config = {
        method: 'POST',
        headers: {
            'Accept': 'application/json',
            'Content-Type': 'application/json'
        },
        body: JSON.stringify({
            email: document.getElementById('login-email').value,
            password: document.getElementById('login-password').value
        })
    };
    const response = await fetch('/login', config);
    const data = await response.json();
    // 将令牌存储在客户端（例如sessionStorage）
    sessionStorage.setItem('token', data.token);
    document.body.innerHTML += `<p>${JSON.stringify(data)}</p>`;
}
```

![](img/6c68f1f2b6558d155ff370ad0b7cb864_124.png)

### 3.3 创建受保护的路由 🛡️

![](img/6c68f1f2b6558d155ff370ad0b7cb864_125.png)

我们将创建一个中间件来验证JWT，并保护一个特定的路由。

**`api/user-routes.js` 中的验证中间件和受保护路由：**

```javascript
// JWT验证中间件
function verifyToken(req, res, next) {
    if (!req.headers.authorization) {
        return res.status(401).json({ message: 'Unauthorized request' });
    }
    const token = req.headers.authorization.split(' ')[1];
    if (!token) {
        return res.status(401).json({ message: 'Unauthorized request' });
    }
    try {
        const payload = jwt.verify(token, 'secret_key');
        req.userId = payload.subject; // 将用户ID附加到请求对象
        next();
    } catch (err) {
        return res.status(401).json({ message: 'Unauthorized request' });
    }
}

// 受保护的路由
router.get('/special', verifyToken, (req, res) => {
    res.json({ user: req.userId });
});
```

![](img/6c68f1f2b6558d155ff370ad0b7cb864_127.png)

![](img/6c68f1f2b6558d155ff370ad0b7cb864_128.png)

**前端访问受保护路由：**

![](img/6c68f1f2b6558d155ff370ad0b7cb864_130.png)

```javascript
async function testProtected() {
    const token = sessionStorage.getItem('token');
    const config = {
        method: 'GET',
        headers: {
            'Authorization': 'Bearer ' + token
        }
    };
    const response = await fetch('/special', config);
    const data = await response.json();
    document.body.innerHTML += `<p>${JSON.stringify(data)}</p>`;
}
```

![](img/6c68f1f2b6558d155ff370ad0b7cb864_132.png)

![](img/6c68f1f2b6558d155ff370ad0b7cb864_134.png)

**安全提醒：** 此示例将令牌存储在 `sessionStorage` 中仅用于演示。在实际应用中，需要考虑令牌的存储安全性和过期策略，例如使用HttpOnly Cookie或短期的内存存储，以降低XSS攻击导致令牌被盗的风险。

---

## 总结 🎉

在本教程中，我们一起学习了如何构建一个基础的全栈应用：

1.  **环境搭建**：我们部署了本地的MongoDB服务器和Express Web服务器。
2.  **数据库连接**：使用Mongoose库连接Express应用到MongoDB，并定义了`User`数据模型。
3.  **CRUD操作**：我们实现了完整的创建、读取、更新和删除端点，并通过前端界面进行了测试。
4.  **JWT身份验证**：我们引入了基于JWT的无状态认证，实现了登录接口、令牌签发以及受保护路由的访问控制。

这个应用展示了客户端、服务器和数据库三层架构之间的基本通信模式。你可以以此为基础，添加更复杂的业务逻辑、改进错误处理、美化前端界面，并将其部署到生产环境（如使用Heroku和MongoDB Atlas）。

**下一步建议：**
*   为服务器添加全面的错误处理（`try...catch`）。
*   防止数据重复（如唯一邮箱）。
*   使用环境变量管理敏感配置（如JWT密钥、数据库URL）。
*   为令牌设置合理的过期时间。
*   将应用部署到云平台，体验完整的开发流程。

![](img/6c68f1f2b6558d155ff370ad0b7cb864_136.png)

祝你构建出功能强大的Web应用！