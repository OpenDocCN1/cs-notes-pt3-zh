# HTTP连接比较

# Nonpersistent HTTP
(非持久连接)

+   - 一个连接只传输一个对象
+   - Server发送响应后，即关闭连接
+   - 优点：简单
+   - 缺点：
+     - 每个对象都会有2×RTT
+     - 建立TCP连接需要OS开销
+     - 用户经常需要同时建立多个TCP连接
+   - HTTP 1.0

# Persistent HTTP
(持久连接)

+   - 一个TCP连接可以传输多个对象
+   - 优点：发送完响应后，Server不关闭连接，在一个TCP连接上可以传输多个对象
+   - HTTP 1.1