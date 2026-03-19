# 014：静态Web服务器 🖥️

![](img/afa810535f6f5d5fb2aff4ff22d428ca_1.png)

在本节课中，我们将从前端转向后端，开始探索如何构建自己的Web服务器。我们将学习Node.js和NPM的基础知识，并从头开始构建一个能够处理HTTP请求、发送响应并支持不同状态码的静态Web服务器。

---

## 概述 📋

我们将从零开始，逐步构建一个功能完整的静态Web服务器。这个服务器将能够监听客户端请求，解析请求的URL路径，检查文件是否存在，并根据结果返回相应的HTTP状态码（如200成功、404未找到、302重定向、500服务器错误）和内容。通过这个过程，我们将深入理解Web服务器的工作原理。

---

## 1. 引言与核心概念

![](img/afa810535f6f5d5fb2aff4ff22d428ca_3.png)

在开始编码之前，我们需要理解几个核心概念。

![](img/afa810535f6f5d5fb2aff4ff22d428ca_5.png)

**Node.js** 是一个JavaScript运行时环境，它允许我们在操作系统层面（例如通过终端）运行JavaScript代码，而不仅仅局限于浏览器环境。这为我们打开了构建各种应用程序（包括Web服务器）的大门。

**NPM**（Node Package Manager）是Node.js的包管理器。它用于安装项目依赖的外部模块，并可以运行我们定义的脚本，是管理Node.js项目的标准工具。

一个**Web服务器**是一个应用程序，它监听来自客户端（如浏览器）的HTTP请求，并发送回HTTP响应。

在构建服务器时，我们需要处理：
*   **路由**：应用程序的端点（URL）如何响应客户端请求。
*   **MIME类型**：指示所传输文档性质和格式的标准（例如 `text/html` 代表HTML文档，`image/jpeg` 代表JPEG图片）。
*   **HTTP状态码**：服务器响应的一部分，用于表明请求的成功或失败状态（例如200成功，404未找到）。

---

![](img/afa810535f6f5d5fb2aff4ff22d428ca_7.png)

## 2. 迭代一：使用Node部署“Hello World”服务器

![](img/afa810535f6f5d5fb2aff4ff22d428ca_9.png)

上一节我们介绍了核心概念，本节中我们来看看如何构建一个最简单的Web服务器。

![](img/afa810535f6f5d5fb2aff4ff22d428ca_11.png)

我们的目标是创建一个服务器，监听请求并返回“Hello World”文本。

**步骤如下：**

1.  **导入HTTP模块**：Node.js内置了`http`模块，用于创建服务器和处理HTTP事务。
    ```javascript
    const http = require('http');
    ```
2.  **配置服务器**：定义服务器监听的主机名和端口。
    ```javascript
    const hostname = 'localhost';
    const port = 3000;
    ```
3.  **创建请求处理器**：这是一个回调函数，当服务器收到请求时会被调用。它接收`request`和`response`对象。
    ```javascript
    const httpHandler = (request, response) => {
      response.statusCode = 200; // 设置状态码为200（成功）
      response.setHeader('Content-Type', 'text/plain'); // 设置响应头，内容类型为纯文本
      response.end('Hello World\n'); // 结束响应并发送数据
    };
    ```
4.  **创建服务器并启动监听**：使用`http`模块创建服务器实例，并让它开始监听指定端口。
    ```javascript
    const server = http.createServer(httpHandler);
    server.listen(port, hostname, () => {
      console.log(`Server running at http://${hostname}:${port}/`);
    });
    ```

将以上代码保存为`server.js`，在终端中运行 `node server.js`，然后在浏览器中访问 `http://localhost:3000/`，你将看到“Hello World”。

**关键点**：必须调用`response.end()`来结束响应，否则客户端会一直等待。

---

## 3. 迭代二：使用NPM部署服务器

上一节我们直接使用Node运行脚本，本节中我们来看看如何使用NPM来管理和启动我们的应用，这是更标准的项目做法。

![](img/afa810535f6f5d5fb2aff4ff22d428ca_13.png)

NPM会寻找项目根目录下的`package.json`文件来获取配置信息。

![](img/afa810535f6f5d5fb2aff4ff22d428ca_15.png)

**步骤如下：**

1.  **创建`package.json`文件**：在项目目录下创建此文件，它是一个JSON格式的配置文件。
    ```json
    {
      "name": "web-server",
      "version": "0.0.1",
      "description": "A simple static web server",
      "main": "server.js",
      "author": "Your Name",
      "scripts": {
        "start": "node server.js"
      }
    }
    ```
2.  **使用NPM启动**：在终端中，进入项目目录并运行 `npm start`。NPM会读取`package.json`中的`scripts`配置，执行`node server.js`命令。

![](img/afa810535f6f5d5fb2aff4ff22d428ca_17.png)

现在，我们有了一个更规范的项目结构，并且可以通过NPM统一管理启动命令。

![](img/afa810535f6f5d5fb2aff4ff22d428ca_19.png)

---

## 4. 迭代三：解析URL路径中的文件名

我们的服务器目前只响应根路径。本节中我们来看看如何解析客户端请求的URL路径，以确定他们想要访问哪个文件。

我们需要使用Node.js内置的`url`和`path`模块。

**步骤如下：**

![](img/afa810535f6f5d5fb2aff4ff22d428ca_21.png)

1.  **导入所需模块**。
    ```javascript
    const url = require('url');
    const path = require('path');
    ```
2.  **重构HTTP处理器**：在处理器中，解析请求的URL，获取路径名，并将其与当前工作目录拼接，得到完整的本地文件路径。
    ```javascript
    const httpHandler = (request, response) => {
      const parsedUrl = url.parse(request.url);
      const pathname = `.${parsedUrl.pathname}`; // `./` 开头表示相对路径
      const filename = path.join(process.cwd(), pathname); // 拼接完整路径

      console.log(`URL requested: ${parsedUrl.pathname}`);
      console.log(`File path: ${filename}`);
      // 注意：此时尚未发送响应，浏览器会持续加载
    };
    ```

运行服务器并访问 `http://localhost:3000/index.html`，你将在终端看到输出的URL和计算出的文件路径。这证明我们已经能够正确解析客户端的请求目标。

![](img/afa810535f6f5d5fb2aff4ff22d428ca_23.png)

![](img/afa810535f6f5d5fb2aff4ff22d428ca_24.png)

---

![](img/afa810535f6f5d5fb2aff4ff22d428ca_26.png)

![](img/afa810535f6f5d5fb2aff4ff22d428ca_28.png)

## 5. 迭代四：处理404“文件未找到”错误

![](img/afa810535f6f5d5fb2aff4ff22d428ca_30.png)

上一节我们学会了解析路径，本节中我们来看看当请求的文件不存在时，如何向客户端返回一个标准的404错误。

![](img/afa810535f6f5d5fb2aff4ff22d428ca_32.png)

我们需要使用`fs`（文件系统）模块来检查文件是否存在。

![](img/afa810535f6f5d5fb2aff4ff22d428ca_34.png)

![](img/afa810535f6f5d5fb2aff4ff22d428ca_36.png)

**步骤如下：**

1.  **导入`fs`模块**。
    ```javascript
    const fs = require('fs');
    ```
2.  **重构HTTP处理器**：尝试获取文件状态。如果文件不存在（抛出异常），则调用一个辅助函数返回404错误。
    ```javascript
    const httpHandler = (request, response) => {
      // ... 解析URL和路径的代码 ...
      try {
        const stats = fs.statSync(filename); // 同步获取文件状态
        // 文件存在，后续处理（下一步实现）
      } catch (error) {
        fileNotFound(response); // 文件不存在，返回404
        return;
      }
    };
    ```
3.  **创建`fileNotFound`辅助函数**：此函数负责构建并发送404响应。
    ```javascript
    const fileNotFound = (response) => {
      response.writeHead(404, { 'Content-Type': 'text/plain' });
      response.write('404 Not Found\n');
      response.end();
    };
    ```

![](img/afa810535f6f5d5fb2aff4ff22d428ca_38.png)

现在，如果你请求一个不存在的文件（如 `http://localhost:3000/nonexistent.html`），服务器将返回“404 Not Found”。

![](img/afa810535f6f5d5fb2aff4ff22d428ca_40.png)

---

![](img/afa810535f6f5d5fb2aff4ff22d428ca_42.png)

![](img/afa810535f6f5d5fb2aff4ff22d428ca_44.png)

![](img/afa810535f6f5d5fb2aff4ff22d428ca_45.png)

## 6. 迭代五：处理200成功并识别MIME类型

当文件存在时，我们需要返回成功响应。本节中我们来看看如何根据文件扩展名确定正确的MIME类型，并返回200状态码。

![](img/afa810535f6f5d5fb2aff4ff22d428ca_47.png)

![](img/afa810535f6f5d5fb2aff4ff22d428ca_48.png)

![](img/afa810535f6f5d5fb2aff4ff22d428ca_49.png)

**步骤如下：**

![](img/afa810535f6f5d5fb2aff4ff22d428ca_51.png)

![](img/afa810535f6f5d5fb2aff4ff22d428ca_52.png)

1.  **定义MIME类型映射字典**：将常见的文件扩展名映射到对应的MIME类型。
    ```javascript
    const mimeTypes = {
      '.html': 'text/html',
      '.jpeg': 'image/jpeg',
      '.jpg': 'image/jpeg',
      '.png': 'image/png',
      '.js': 'text/javascript',
      '.css': 'text/css'
    };
    ```
2.  **重构HTTP处理器**：在文件状态获取成功后，检查它是否是一个普通文件。如果是，则调用`serveFile`辅助函数。
    ```javascript
    if (stats.isFile()) {
      serveFile(response, filename);
    }
    // 注意：我们暂时不处理目录情况
    ```
3.  **创建`serveFile`辅助函数**：此函数根据文件扩展名设置正确的`Content-Type`头，并返回200状态码。
    ```javascript
    const serveFile = (response, filename) => {
      const ext = path.extname(filename); // 获取文件扩展名，如 `.html`
      const mimeType = mimeTypes[ext] || 'text/plain'; // 查找MIME类型，默认为纯文本

      response.writeHead(200, { 'Content-Type': mimeType });
      response.write(`200 Success - Serving file as ${mimeType}\n`);
      response.end();
    };
    ```

![](img/afa810535f6f5d5fb2aff4ff22d428ca_54.png)

创建一个`index.html`文件，然后访问它。服务器将返回200状态码，并告诉你它识别出这是一个`text/html`类型的文件。

![](img/afa810535f6f5d5fb2aff4ff22d428ca_56.png)

![](img/afa810535f6f5d5fb2aff4ff22d428ca_58.png)

![](img/afa810535f6f5d5fb2aff4ff22d428ca_60.png)

---

![](img/afa810535f6f5d5fb2aff4ff22d428ca_62.png)

![](img/afa810535f6f5d5fb2aff4ff22d428ca_64.png)

## 7. 迭代六：提供HTML文件内容给浏览器

上一节我们识别了文件类型，本节中我们来看看如何将文件的实际内容读取并发送给客户端浏览器进行渲染。

![](img/afa810535f6f5d5fb2aff4ff22d428ca_66.png)

![](img/afa810535f6f5d5fb2aff4ff22d428ca_68.png)

我们将使用`fs`模块创建可读流，并将文件内容“管道”传输到响应对象中。

**重构`serveFile`函数：**
```javascript
const serveFile = (response, filename) => {
  const ext = path.extname(filename);
  const mimeType = mimeTypes[ext] || 'text/plain';

  response.writeHead(200, { 'Content-Type': mimeType });

  // 创建文件可读流，并将其管道传输到响应中
  const fileStream = fs.createReadStream(filename);
  fileStream.pipe(response);
};
```

![](img/afa810535f6f5d5fb2aff4ff22d428ca_70.png)

![](img/afa810535f6f5d5fb2aff4ff22d428ca_72.png)

现在，当你访问 `http://localhost:3000/index.html` 时，浏览器不仅收到200状态码和正确的`Content-Type`头，还会收到`index.html`文件的内容并渲染它。

---

![](img/afa810535f6f5d5fb2aff4ff22d428ca_74.png)

![](img/afa810535f6f5d5fb2aff4ff22d428ca_76.png)

![](img/afa810535f6f5d5fb2aff4ff22d428ca_78.png)

![](img/afa810535f6f5d5fb2aff4ff22d428ca_80.png)

## 8. 迭代七：实现302重定向

通常，访问一个目录（如根路径`/`）时，Web服务器会默认返回该目录下的`index.html`文件。本节中我们来看看如何使用302状态码实现重定向。

![](img/afa810535f6f5d5fb2aff4ff22d428ca_82.png)

我们需要在HTTP处理器中检查请求的目标是否是一个目录。

![](img/afa810535f6f5d5fb2aff4ff22d428ca_84.png)

![](img/afa810535f6f5d5fb2aff4ff22d428ca_86.png)

**步骤如下：**

1.  **重构HTTP处理器中的条件判断**：在文件状态检查成功后，区分它是文件还是目录。
    ```javascript
    if (stats.isFile()) {
      serveFile(response, filename);
    } else if (stats.isDirectory()) {
      serveIndex(response); // 是目录，重定向到index.html
    }
    ```
2.  **创建`serveIndex`辅助函数**：此函数发送302状态码，并在响应头中指定重定向的目标位置。
    ```javascript
    const serveIndex = (response) => {
      response.writeHead(302, { 'Location': '/index.html' });
      response.end();
    };
    ```

![](img/afa810535f6f5d5fb2aff4ff22d428ca_88.png)

现在，当你直接访问 `http://localhost:3000/`（根目录）时，服务器会返回302重定向响应，浏览器会自动跳转到 `/index.html` 并加载页面。

![](img/afa810535f6f5d5fb2aff4ff22d428ca_90.png)

---

![](img/afa810535f6f5d5fb2aff4ff22d428ca_92.png)

![](img/afa810535f6f5d5fb2aff4ff22d428ca_93.png)

## 9. 迭代八：处理500服务器内部错误

![](img/afa810535f6f5d5fb2aff4ff22d428ca_95.png)

![](img/afa810535f6f5d5fb2aff4ff22d428ca_97.png)

我们已经处理了客户端错误（404）和成功情况（200，302）。本节中我们来看看最后一个常见的状态码——500，它表示服务器端发生了内部错误。

![](img/afa810535f6f5d5fb2aff4ff22d428ca_99.png)

我们将在逻辑中添加一个最终的`else`分支，作为意外情况的兜底处理。

**步骤如下：**

![](img/afa810535f6f5d5fb2aff4ff22d428ca_101.png)

1.  **完善HTTP处理器中的条件判断**：添加`else`分支来处理既不是文件也不是目录的意外情况（例如，由于权限问题无法访问）。
    ```javascript
    if (stats.isFile()) {
      serveFile(response, filename);
    } else if (stats.isDirectory()) {
      serveIndex(response);
    } else {
      serverError(response); // 意外情况，触发服务器错误
    }
    ```
2.  **创建`serverError`辅助函数**：此函数发送500状态码。
    ```javascript
    const serverError = (response) => {
      response.writeHead(500, { 'Content-Type': 'text/plain' });
      response.write('500 Internal Server Error\n');
      response.end();
    };
    ```

![](img/afa810535f6f5d5fb2aff4ff22d428ca_103.png)

![](img/afa810535f6f5d5fb2aff4ff22d428ca_104.png)

![](img/afa810535f6f5d5fb2aff4ff22d428ca_106.png)

**注意**：在正常运行的代码中，这个分支很难被触发。你可以通过故意引入逻辑错误（例如，错误地判断文件类型）来测试这个功能。这是一个重要的安全网，用于处理不可预见的服务器端问题。

![](img/afa810535f6f5d5fb2aff4ff22d428ca_108.png)

---

## 总结 🎉

![](img/afa810535f6f5d5fb2aff4ff22d428ca_110.png)

在本节课中，我们一起学习了如何使用纯Node.js和其核心模块构建一个静态Web服务器。我们完成了以下任务：

1.  使用`http`模块创建了服务器实例并监听端口。
2.  使用`url`和`path`模块解析客户端请求的URL路径。
3.  使用`fs`模块检查文件是否存在、读取文件内容。
4.  根据不同的情况，向客户端返回了相应的HTTP状态码：200（成功）、404（未找到）、302（重定向）和500（服务器错误）。
5.  根据文件扩展名设置了正确的`Content-Type`（MIME类型）响应头。
6.  使用NPM来管理项目并启动脚本。

![](img/afa810535f6f5d5fb2aff4ff22d428ca_112.png)

通过这个循序渐进的构建过程，我们深入理解了Web服务器处理请求-响应周期的基本机制。在接下来的课程中，我们将使用Express框架来重构这个服务器。Express会帮我们处理大量底层细节，让我们能够更专注于应用程序的业务逻辑，用更少的代码实现更强大的功能。