# 4.4 网络控制报文协议 ICMP

# 二、ICMP报文类型

+   - 差错报告报文
+     - Destination unreachable: 终点不可达，由路由器或主机无法传输报文时向源主机发送此报文
+     - Source quench: 源点抑制，发送由路由器或主机对拥塞丢弃报文时，向源主机发送此报文，使其放慢发送速度
+     - Time exceeded: 超时时，由路由器或TTL值减为0的报文时，向源主机发送此报文
+     - Parameter problem: 参数问题，路由器或主机收到的数据报中头部有非零字段时，去往源主机，并向源主机发送此报文
+     - Redirect: 重定向，若路由器向主机发送报文时发现由改变网段下此数据报经过路由外的路由器

+   - 询问报文
+     - Echo request / reply: 回声请求/回复，用于测试网络连通性
+     - Timestamp request / reply: 时间戳请求/回复，可用于时间同步

# 4.3 划分子网与超网

# 2010年的一道考研题：

若路由器R因为拥塞丢弃IP分组，则此时R可向发出该IP分组的源主机的ICMP报文的类型是（ ）
A. 路由重定向  B. 目的不可达
C. 源抑制  D. 超时

# 三、ICMP应用举例(1/2)

+   - Ping
+     - 用来测试两个主机之间的连通性
+     - 采用ICMP echo request / reply报文
+     - 向目标主机发送ICMP echo request报文，对方收到后回送ICMP echo reply，根据收到的回送报文判断两台主机之间是否连通

```
D:\>ping news.sina.com.cn
Pinging hydra.sina.com.cn [218.30.108.63] with 32 bytes of data:
Reply from 218.30.108.63: bytes=32 time=11ms TTL=54
Reply from 218.30.108.63: bytes=32 time=12ms TTL=54
Reply from 218.30.108.63: bytes=32 time=12ms TTL=54
Reply from 218.30.108.63: bytes=32 time=12ms TTL=54

Ping statistics for 218.30.108.63:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 11ms, Maximum = 12ms, Average = 11ms
```

# 三、ICMP应用举例(2/2)

+   - Traceroute / Tracert
+     - 用来测试到另一台主机所经过的路由信息
+     - 采用ICMP超时报文实现
+     - 发送不同TTL值的报文，其IP报头中的TTL字段分别设为1,2,3,...,直到到达目的主机
+     - 接收到超时报文上的源路由器会回送ICMP超时报文，从该报文可得知源路由器的IP地址

```
D:\tracert -d hydra.sina.com.cn
Tracing route to hydra.sina.com.cn [218.30.108.67]
over a maximum of 30 hops:

  1    <1 ms    <1 ms    <1 ms  192.168.1.1
  2     2 ms     2 ms     2 ms  218.143.128.128
  3    13 ms    13 ms    13 ms  218.143.128.1
  4    13 ms    13 ms    13 ms  218.141.131.13
  5    15 ms    15 ms    15 ms  218.141.130.110
  6    21 ms    21 ms    21 ms  220.181.16.130
  7    21 ms    21 ms    21 ms  218.30.25.237
  8    21 ms    21 ms    21 ms  218.30.26.70
  9    10 ms    10 ms    10 ms  218.30.104.42
 10    10 ms    10 ms    10 ms  218.30.108.67
Trace complete.
```

# 4.5 路由算法及协议

# 4.5 路由算法及协议

# 一、路由算法简介(1/4)

+   - 在网络中，路由器负责转发分组，路由信息是路由协议产生的信息，路由算法是路由协议的基础和核心
+   - 路由算法是用来生成路由信息(路由表)，不转发分组的
+   - 理想的路由算法应具备的特性:
+     - 必须是最优的和合理的，携带出的路由能够进行网寻址
+     - 在计算上应简单，不增加过多开销
+     - 有自适应性，能根据网络状况和网络拓扑的变化调整路由
+     - 反应灵敏性，通信链路不断稳定，能快速收敛
+     - 适应性强，对应各种网络公平
+     - 应该是稳定的，能找出好的路由(时延最小，吞吐量最大)

不存在理想的路由需求可能各有侧重，且网络环境不断变化，因此不存在一种绝对的最优路由算法

# 4.5 路由算法及协议

# 一、路由算法简介(2/4)

# 4.5 路由算法及协议

# 一、路由算法简介(3/4)