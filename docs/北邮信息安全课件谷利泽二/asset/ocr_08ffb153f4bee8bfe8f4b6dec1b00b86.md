# 包过滤检测的内容

数据包过滤一般要检查网络层的IP头和传输层的头：

+   - IP源地址
+   - IP目标地址
+   - 协议类型（TCP包、UDP包和ICMP包）
+   - TCP或UDP包的目的端口
+   - TCP或UDP包的源端口
+   - ICMP消息类型
+   - TCP包头的ACK位
+   - TCP包的序列号、IP校验和等