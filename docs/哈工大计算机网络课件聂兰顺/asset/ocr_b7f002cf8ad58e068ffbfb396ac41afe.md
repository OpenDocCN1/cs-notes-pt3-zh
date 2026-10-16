# TCP连接管理

+   TCP sender和receiver在传输数据前需要建立连接

+   初始化TCP变量
+   - Seq. #
+   - Buffer和流量控制信息

+   Client: 连接发起者

```
Socket clientSocket = new Socket("hostname","port number");
```

+   Server: 等待客户连接请求

```
Socket connectionSocket = welcomeSocket.accept();
```

# Three way handshake:

+   Step 1: client host sends TCP SYN segment to server
+   - specifies initial seq #
+   - no data

+   Step 2: server host receives SYN, replies with SYNACK segment
+   - server allocates buffers
+   - specifies server initial seq. #

Step 3: client receives SYNACK, replies with ACK segment, which may contain data