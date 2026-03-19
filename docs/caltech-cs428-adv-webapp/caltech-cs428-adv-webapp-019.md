# 019：用户登录（第一部分） 👨‍💻

![](img/517e2071587e8157cfa6c9556183a85f_0.png)

![](img/517e2071587e8157cfa6c9556183a85f_2.png)

![](img/517e2071587e8157cfa6c9556183a85f_4.png)

在本节课中，我们将学习如何为Web应用实现用户认证系统。我们将从上一节引入的会话（Session）概念出发，逐步构建一个完整的登录、注册和登出流程，并确保用户密码的安全存储。

![](img/517e2071587e8157cfa6c9556183a85f_6.png)

上一节我们介绍了如何使用会话ID来识别客户端，本节中我们来看看如何利用会话来实现用户认证。

![](img/517e2071587e8157cfa6c9556183a85f_8.png)

## 概述

![](img/517e2071587e8157cfa6c9556183a85f_10.png)

![](img/517e2071587e8157cfa6c9556183a85f_12.png)

我们将使用 `Passport.js` 这个Node.js中间件来处理用户认证。具体步骤包括：
1.  安装并配置 `passport` 和 `passport-local` 模块。
2.  在用户模型中添加查找用户的功能。
3.  创建Passport配置模块，定义本地认证策略。
4.  在应用和控制器中集成Passport。
5.  实现序列化和反序列化用户，以便在请求中访问用户数据。
6.  使用 `express-flash` 显示认证错误信息。
7.  创建中间件来保护路由，防止未授权访问。
8.  实现安全的密码哈希存储（使用 `bcrypt`）。
9.  使用 `.env` 文件保护敏感配置信息。

![](img/517e2071587e8157cfa6c9556183a85f_14.png)

## 配置Passport和用户模型

![](img/517e2071587e8157cfa6c9556183a85f_16.png)

首先，我们需要安装必要的依赖包。

![](img/517e2071587e8157cfa6c9556183a85f_18.png)

```json
// package.json 中添加
"dependencies": {
  "passport": "^0.5.0",
  "passport-local": "^1.0.0"
}
```

接下来，我们在用户模型 `users.model.js` 中添加一个根据键值对查找用户的方法。

```javascript
// users.model.js
findUser(key, value) {
  return this.users.find(user => user[key] === value);
}
```

## 创建Passport配置模块

![](img/517e2071587e8157cfa6c9556183a85f_20.png)

![](img/517e2071587e8157cfa6c9556183a85f_22.png)

![](img/517e2071587e8157cfa6c9556183a85f_24.png)

![](img/517e2071587e8157cfa6c9556183a85f_26.png)

我们创建一个中间件模块 `passport-config.js` 来配置Passport的本地策略。

![](img/517e2071587e8157cfa6c9556183a85f_28.png)

```javascript
// middlewares/passport-config.js
const LocalStrategy = require('passport-local').Strategy;
const passport = require('passport');
const users = require('../models/users.model');

![](img/517e2071587e8157cfa6c9556183a85f_30.png)

![](img/517e2071587e8157cfa6c9556183a85f_32.png)

![](img/517e2071587e8157cfa6c9556183a85f_34.png)

const formNames = {
  usernameField: 'email',
  passwordField: 'password'
};

const authenticateUser = async (email, password, done) => {
  const user = users.findUser('email', email);
  if (!user) {
    console.log('No user with that email');
    return done(null, false, { message: 'No user with that email' });
  }
  try {
    if (await bcrypt.compare(password, user.password)) {
      console.log('User authenticated');
      return done(null, user);
    } else {
      console.log('Password incorrect');
      return done(null, false, { message: 'Password incorrect' });
    }
  } catch (e) {
    return done(e);
  }
};

const strategy = new LocalStrategy(formNames, authenticateUser);
passport.use(strategy);

passport.serializeUser((user, done) => {
  done(null, user.id);
});

passport.deserializeUser((id, done) => {
  const user = users.findUser('id', id);
  done(null, user);
});

![](img/517e2071587e8157cfa6c9556183a85f_36.png)

![](img/517e2071587e8157cfa6c9556183a85f_38.png)

module.exports = passport;
```

![](img/517e2071587e8157cfa6c9556183a85f_40.png)

![](img/517e2071587e8157cfa6c9556183a85f_42.png)

## 在应用中集成Passport

在 `app.js` 中，我们导入配置好的Passport并初始化它，同时启用会话支持。

![](img/517e2071587e8157cfa6c9556183a85f_44.png)

```javascript
// app.js
const passport = require('./middlewares/passport-config');

![](img/517e2071587e8157cfa6c9556183a85f_46.png)

![](img/517e2071587e8157cfa6c9556183a85f_47.png)

![](img/517e2071587e8157cfa6c9556183a85f_49.png)

// 在 express-session 之后，定义路由之前
app.use(passport.initialize());
app.use(passport.session());
```

![](img/517e2071587e8157cfa6c9556183a85f_51.png)

![](img/517e2071587e8157cfa6c9556183a85f_53.png)

![](img/517e2071587e8157cfa6c9556183a85f_55.png)

![](img/517e2071587e8157cfa6c9556183a85f_57.png)

在控制器 `users.controller.js` 中，我们重构登录路由的处理逻辑，使用Passport进行认证。

![](img/517e2071587e8157cfa6c9556183a85f_59.png)

```javascript
// controllers/users.controller.js
const passport = require('../middlewares/passport-config');

![](img/517e2071587e8157cfa6c9556183a85f_61.png)

![](img/517e2071587e8157cfa6c9556183a85f_63.png)

![](img/517e2071587e8157cfa6c9556183a85f_65.png)

exports.postLogin = (req, res, next) => {
  const config = {
    successRedirect: '/',
    failureRedirect: '/login',
    failureFlash: true
  };
  const authFunction = passport.authenticate('local', config);
  authFunction(req, res, next);
};
```

![](img/517e2071587e8157cfa6c9556183a85f_66.png)

![](img/517e2071587e8157cfa6c9556183a85f_68.png)

![](img/517e2071587e8157cfa6c9556183a85f_70.png)

![](img/517e2071587e8157cfa6c9556183a85f_72.png)

## 序列化用户与访问用户数据

![](img/517e2071587e8157cfa6c9556183a85f_74.png)

![](img/517e2071587e8157cfa6c9556183a85f_76.png)

![](img/517e2071587e8157cfa6c9556183a85f_77.png)

![](img/517e2071587e8157cfa6c9556183a85f_79.png)

Passport通过序列化和反序列化将用户信息存入会话。我们在配置模块中已经定义了相关方法。现在，我们可以在受保护的页面（如首页）中访问用户数据。

![](img/517e2071587e8157cfa6c9556183a85f_81.png)

![](img/517e2071587e8157cfa6c9556183a85f_83.png)

![](img/517e2071587e8157cfa6c9556183a85f_85.png)

![](img/517e2071587e8157cfa6c9556183a85f_86.png)

```javascript
// controllers/users.controller.js
exports.getIndex = (req, res) => {
  res.render('index', { name: req.user.name });
};
```

![](img/517e2071587e8157cfa6c9556183a85f_88.png)

![](img/517e2071587e8157cfa6c9556183a85f_90.png)

![](img/517e2071587e8157cfa6c9556183a85f_92.png)

## 使用Flash消息和路由保护

![](img/517e2071587e8157cfa6c9556183a85f_94.png)

我们安装 `express-flash` 来在认证失败时向用户显示错误信息。

![](img/517e2071587e8157cfa6c9556183a85f_96.png)

```json
// package.json
"express-flash": "^0.0.2"
```

![](img/517e2071587e8157cfa6c9556183a85f_98.png)

在 `app.js` 中启用它，并在登录EJS模板中显示错误。

![](img/517e2071587e8157cfa6c9556183a85f_100.png)

![](img/517e2071587e8157cfa6c9556183a85f_101.png)

![](img/517e2071587e8157cfa6c9556183a85f_103.png)

```ejs
<!-- views/login.ejs -->
<% if (messages.error) { %>
  <p><%= messages.error %></p>
<% } %>
```

![](img/517e2071587e8157cfa6c9556183a85f_105.png)

为了保护路由，我们创建中间件 `auth.js`。

![](img/517e2071587e8157cfa6c9556183a85f_107.png)

![](img/517e2071587e8157cfa6c9556183a85f_109.png)

```javascript
// middlewares/auth.js
exports.checkAuthenticated = (req, res, next) => {
  if (req.isAuthenticated()) {
    return next();
  }
  res.redirect('/login');
};

![](img/517e2071587e8157cfa6c9556183a85f_111.png)

![](img/517e2071587e8157cfa6c9556183a85f_113.png)

exports.checkNotAuthenticated = (req, res, next) => {
  if (req.isAuthenticated()) {
    return res.redirect('/');
  }
  next();
};
```

![](img/517e2071587e8157cfa6c9556183a85f_115.png)

然后在路由文件中应用这些中间件。

![](img/517e2071587e8157cfa6c9556183a85f_117.png)

![](img/517e2071587e8157cfa6c9556183a85f_119.png)

![](img/517e2071587e8157cfa6c9556183a85f_121.png)

```javascript
// routes/users.routes.js
const { checkAuthenticated, checkNotAuthenticated } = require('../middlewares/auth');

![](img/517e2071587e8157cfa6c9556183a85f_123.png)

![](img/517e2071587e8157cfa6c9556183a85f_125.png)

![](img/517e2071587e8157cfa6c9556183a85f_127.png)

![](img/517e2071587e8157cfa6c9556183a85f_129.png)

![](img/517e2071587e8157cfa6c9556183a85f_130.png)

router.get('/', checkAuthenticated, usersController.getIndex);
router.get('/login', checkNotAuthenticated, usersController.getLogin);
router.get('/register', checkNotAuthenticated, usersController.getRegister);
```

![](img/517e2071587e8157cfa6c9556183a85f_132.png)

![](img/517e2071587e8157cfa6c9556183a85f_134.png)

![](img/517e2071587e8157cfa6c9556183a85f_135.png)

## 实现登出和密码安全

![](img/517e2071587e8157cfa6c9556183a85f_137.png)

![](img/517e2071587e8157cfa6c9556183a85f_139.png)

![](img/517e2071587e8157cfa6c9556183a85f_140.png)

登出功能非常简单，Passport在请求对象上提供了 `logout()` 方法。

![](img/517e2071587e8157cfa6c9556183a85f_142.png)

```javascript
// controllers/users.controller.js
exports.postLogout = (req, res) => {
  req.logout();
  res.redirect('/login');
};
```

![](img/517e2071587e8157cfa6c9556183a85f_144.png)

![](img/517e2071587e8157cfa6c9556183a85f_146.png)

为了安全，我们使用 `bcrypt` 对密码进行哈希处理，而不是存储明文。

![](img/517e2071587e8157cfa6c9556183a85f_148.png)

![](img/517e2071587e8157cfa6c9556183a85f_150.png)

![](img/517e2071587e8157cfa6c9556183a85f_152.png)

![](img/517e2071587e8157cfa6c9556183a85f_154.png)

![](img/517e2071587e8157cfa6c9556183a85f_156.png)

![](img/517e2071587e8157cfa6c9556183a85f_157.png)

```json
// package.json
"bcrypt": "^5.0.0"
```

![](img/517e2071587e8157cfa6c9556183a85f_159.png)

![](img/517e2071587e8157cfa6c9556183a85f_161.png)

![](img/517e2071587e8157cfa6c9556183a85f_163.png)

在用户模型和Passport配置中更新相关代码。

![](img/517e2071587e8157cfa6c9556183a85f_165.png)

![](img/517e2071587e8157cfa6c9556183a85f_167.png)

```javascript
// users.model.js
const bcrypt = require('bcrypt');
async add(name, email, password) {
  const hashedPassword = await bcrypt.hash(password, 10);
  const id = shortid.generate();
  this.users.push({ id, name, email, password: hashedPassword });
  return id;
}
```

## 使用环境变量保护密钥

![](img/517e2071587e8157cfa6c9556183a85f_169.png)

![](img/517e2071587e8157cfa6c9556183a85f_171.png)

![](img/517e2071587e8157cfa6c9556183a85f_173.png)

![](img/517e2071587e8157cfa6c9556183a85f_175.png)

![](img/517e2071587e8157cfa6c9556183a85f_177.png)

![](img/517e2071587e8157cfa6c9556183a85f_178.png)

最后，我们使用 `dotenv` 模块将敏感信息（如会话密钥）移出代码，存入 `.env` 文件。

![](img/517e2071587e8157cfa6c9556183a85f_180.png)

![](img/517e2071587e8157cfa6c9556183a85f_182.png)

```json
// package.json
"dotenv": "^10.0.0"
```

![](img/517e2071587e8157cfa6c9556183a85f_184.png)

![](img/517e2071587e8157cfa6c9556183a85f_186.png)

![](img/517e2071587e8157cfa6c9556183a85f_188.png)

```javascript
// app.js
if (process.env.NODE_ENV !== 'production') {
  require('dotenv').config();
}
// ...
app.use(session({
  secret: process.env.SESSION_SECRET,
  // ...
}));
```

![](img/517e2071587e8157cfa6c9556183a85f_190.png)

创建 `.env` 文件并添加到 `.gitignore` 中。

```bash
# .env
SESSION_SECRET=your_secret_word_here
```

![](img/517e2071587e8157cfa6c9556183a85f_192.png)

![](img/517e2071587e8157cfa6c9556183a85f_194.png)

```bash
# .gitignore
node_modules
.env
```

![](img/517e2071587e8157cfa6c9556183a85f_196.png)

## 总结

![](img/517e2071587e8157cfa6c9556183a85f_198.png)

本节课中我们一起学习了如何构建一个完整的用户认证系统。我们从配置Passport开始，实现了用户登录、注册和登出功能，并利用会话保持了用户状态。我们通过中间件保护了路由，确保只有授权用户才能访问特定页面。为了提高安全性，我们使用 `bcrypt` 对密码进行哈希处理，并使用 `.env` 文件保护了应用的敏感配置信息。你现在已经拥有了一个具备基本生产级安全考虑的认证系统骨架。