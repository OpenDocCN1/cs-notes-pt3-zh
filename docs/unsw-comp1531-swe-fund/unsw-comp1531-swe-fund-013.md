# 013：HTTP服务器 part1 🖥️

![](img/f4fa3a08b53724cfa2310f0aa5a0d0bb_1.png)

![](img/f4fa3a08b53724cfa2310f0aa5a0d0bb_3.png)


在本节课中，我们将要学习HTTP服务器的基础知识。这是课程中最重要的讲座之一，标志着课程前半段较难内容的结束。我们将从宏观的网络概念开始，逐步深入到如何使用JavaScript构建一个简单的HTTP服务器。

## 概述

本节课是HTTP服务讲座的第一部分。我们不会一次性涵盖所有内容，而是先建立一个基础，以便在后续讲座中更深入地探讨。我们将讨论网络、互联网和万维网的区别，介绍HTTP协议，并最终使用Express库动手创建一个简单的Web服务器。

## 网络、互联网与万维网

在深入HTTP服务器之前，理解几个核心概念的区别非常重要：网络、互联网和万维网。

![](img/f4fa3a08b53724cfa2310f0aa5a0d0bb_7.png)

![](img/f4fa3a08b53724cfa2310f0aa5a0d0bb_9.png)

*   **网络** 是一组能够相互通信的互联计算机。例如，您家中连接到同一个路由器的所有设备就构成了一个网络，即使没有连接外部互联网，它们之间也能通信。
*   **互联网** 是一个全球性的网络基础设施，它将世界各地的计算机网络连接在一起。
*   **万维网** 是互联网的一个子集，特指通过**Web浏览器**（如Chrome、Safari）访问和使用互联网的方式。我们常看到的“WWW”指的就是万维网。

**核心关系公式**：`万维网 ⊂ 互联网 ⊃ 网络`

## 网络协议与HTTP

计算机之间需要通过共同的“语言”或规则进行通信，这些规则称为**网络协议**。

![](img/f4fa3a08b53724cfa2310f0aa5a0d0bb_11.png)

![](img/f4fa3a08b53724cfa2310f0aa5a0d0bb_13.png)

以下是互联网上一些常见的协议：
*   **IMAP/SMTP**: 用于电子邮件收发。
*   **FTP**: 用于文件传输。
*   **SSH**: 用于安全地远程访问另一台计算机。
*   **HTTP**: 超文本传输协议。

**HTTP** 是本节课的重点。它是专门为**Web浏览器**设计的一种协议，规定了如何在网络上发送和接收文档（如网页、图片）。当您在浏览器地址栏输入一个以“http://”开头的URL时，就是在使用HTTP协议。

![](img/f4fa3a08b53724cfa2310f0aa5a0d0bb_15.png)

![](img/f4fa3a08b53724cfa2310f0aa5a0d0bb_17.png)

![](img/f4fa3a08b53724cfa2310f0aa5a0d0bb_19.png)

## 使用Express创建HTTP服务器

![](img/f4fa3a08b53724cfa2310f0aa5a0d0bb_21.png)

我们将使用一个非常流行的Node.js库——**Express**来构建我们自己的HTTP服务器。它每周被下载超过2500万次，以其简洁易用而闻名。

![](img/f4fa3a08b53724cfa2310f0aa5a0d0bb_23.png)

以下是一个最基本的Express服务器代码示例：


![](img/f4fa3a08b53724cfa2310f0aa5a0d0bb_25.png)

![](img/f4fa3a08b53724cfa2310f0aa5a0d0bb_27.png)


![](img/f4fa3a08b53724cfa2310f0aa5a0d0bb_29.png)

![](img/f4fa3a08b53724cfa2310f0aa5a0d0bb_31.png)

```javascript
import express from 'express';

const app = express();
const PORT = 3000;

app.use(express.json());
app.get('/', (req, res) => {
    res.send('Hello World');
});
app.listen(PORT, () => {
    console.log(`Listening on port ${PORT}`);
});
```

让我们来分解这段代码：
1.  `import express from 'express';`: 导入Express库。
2.  `const app = express();`: 创建一个Express应用实例，这就是我们的Web服务器。
3.  `const PORT = 3000;`: 指定服务器监听的端口号（稍后详细解释端口）。
4.  `app.use(express.json());`: 这是一行配置代码，让服务器能够解析JSON格式的数据，目前只需知道需要它。
5.  `app.get('/', ...)`: 这定义了一个**路由**。它告诉服务器：当客户端通过HTTP `GET` 方法访问根路径`/`时，用字符串`Hello World`作为响应。
6.  `app.listen(PORT, ...)`: 这行代码启动服务器，让它开始监听指定端口上的请求。没有这行代码，服务器就不会运行。

![](img/f4fa3a08b53724cfa2310f0aa5a0d0bb_33.png)

## 运行服务器与端口

![](img/f4fa3a08b53724cfa2310f0aa5a0d0bb_35.png)

运行上述代码后，服务器会启动并持续运行（类似于一个无限循环），等待接收请求。

![](img/f4fa3a08b53724cfa2310f0aa5a0d0bb_37.png)

要访问这个服务器，您需要在浏览器中输入地址。由于服务器运行在您的本地机器上，地址是 **`localhost`** 加上端口号，例如：`http://localhost:3000`。

**端口** 是计算机上的一个虚拟“通道”或“门牌号”，不同的网络应用程序可以通过不同的端口同时运行。端口号范围很大（0-65535）。

关于端口选择，有以下惯例：
*   **0-1023**: 知名端口，通常被系统或核心服务占用（如HTTP默认用80，HTTPS用443），开发时避免使用。
*   **1024-49151**: 注册端口，某些应用程序可能会使用。
*   **49152-65535**: 动态或私有端口，通常用于临时或开发用途。



在开发时，建议选择**3000以上**的端口号（如3000, 5000, 8080）。如果在VLab等共享环境中遇到“地址已在使用”的错误，很可能是因为其他同学恰好使用了相同的端口号，只需更换一个端口即可解决。

您可以为不同的路径定义不同的响应：

![](img/f4fa3a08b53724cfa2310f0aa5a0d0bb_42.png)


![](img/f4fa3a08b53724cfa2310f0aa5a0d0bb_44.png)

![](img/f4fa3a08b53724cfa2310f0aa5a0d0bb_45.png)

![](img/f4fa3a08b53724cfa2310f0aa5a0d0bb_47.png)

```javascript
app.get('/hey', (req, res) => {
    res.send('hey');
});
app.get('/bye/bye', (req, res) => {
    res.send('bye bye');
});
```

重启服务器后，访问`http://localhost:3000/hey` 和 `http://localhost:3000/bye/bye` 就会得到相应的响应。

![](img/f4fa3a08b53724cfa2310f0aa5a0d0bb_49.png)

## 总结

![](img/f4fa3a08b53724cfa2310f0aa5a0d0bb_51.png)

本节课我们一起学习了HTTP服务器的基础知识。我们首先区分了网络、互联网和万维网的概念，然后了解到HTTP是万维网上用于传输文档的核心协议。接着，我们使用Express库动手创建了一个简单的HTTP服务器，学会了如何定义路由来处理不同的URL请求，并理解了端口的概念及其在开发环境中的使用注意事项。

![](img/f4fa3a08b53724cfa2310f0aa5a0d0bb_53.png)

![](img/f4fa3a08b53724cfa2310f0aa5a0d0bb_54.png)

![](img/f4fa3a08b53724cfa2310f0aa5a0d0bb_55.png)

![](img/f4fa3a08b53724cfa2310f0aa5a0d0bb_57.png)

![](img/f4fa3a08b53724cfa2310f0aa5a0d0bb_59.png)

这为我们下一节课深入探讨API设计和CRUD操作奠定了坚实的基础。