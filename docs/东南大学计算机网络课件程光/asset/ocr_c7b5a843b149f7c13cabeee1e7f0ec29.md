# ATM网络的工作过程

+   ATM连接的建立过程

![](bbox=[0.04, 0.22, 0.92, 0.7])

用户终端 A

ATM网络

用户终端 B

622Mbps

连接建立阶段

setup

Call proc

connect

Connect ack

setup

Call proc

connect

Connect ack

+   SETUP控制信元：

发送方用固定的虚拟通道（VPI=0，VCI=5）发SETUP，启动ATM连接建立的过程，

携带对方地址以及要求的服务质量（QOS，例如：所需的网络带宽，最大延时要求等）；