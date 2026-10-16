# 传输层中两类传输协议

+   - **TCP (Transport Control Protocol )**
+     面向连接的能够提供可靠的流式数据传输的协议。类似于打电话的过程。
+     **URL, Socket, ServerSocket**等类都使用TCP协议进行网络通讯。

+   - **UDP (User Datagram Protocol )**
+     非面向连接的提供不可靠的数据包式的数据传输的协议。类似于从邮局发送信件的过程。
+     **DatagramPacket, DatagramSocket**等类使用UDP协议进行网络通讯。

注：当对所传输的数据具有时序性和可靠性等要求时，应使用TCP协议；当传输的数据比较简单、对时序等无要求时，UDP协议能发挥更好的作用。