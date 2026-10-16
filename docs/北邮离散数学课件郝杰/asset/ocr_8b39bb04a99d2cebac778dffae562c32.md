# HTTP 的操作过程

![](bbox=[0.22, 0.197, 0.77, 0.433])

+   1. 浏览器分析超链接，如 `http://www.abc.com/example.html`
+   2. 浏览器使用通过 DNS 获得服务器（`www.abc.com`）的 IP 地址
+   3. 浏览器建立到服务器的 TCP 连接
+   4. 浏览器发送 HTTP 请求：`GET /example.html HTTP/1.1`
+   5. 服务器发送 HTTP 响应
+   6. 释放 TCP 连接
+   7. 浏览器显示网页 `example.html`