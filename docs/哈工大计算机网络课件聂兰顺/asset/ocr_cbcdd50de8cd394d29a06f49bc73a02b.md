# BGP基础

BGP会话(session): 两个BGP路由器（“Peers”）交换BGP报文：

+   - 通告去往不同目的前缀（prefix）的路径（“路径向量(path vector)”协议）
+   - 报文交换基于半永久的TCP连接

BGP报文：

+   - OPEN: 与peer建立TCP连接，并认证发送方
+   - UPDATE: 通告新路径(或撤销原路径)
+   - KEEPALIVE: 在无UPDATE时，保活连接；也用于对OPEN请求的确认
+   - NOTIFICATION: 报告先前报文的差错；也被用于关闭连接