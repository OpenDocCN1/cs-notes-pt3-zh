# Internet AS间路由协议: BGP

+   ◆ 边界网关协议BGP (Border Gateway Protocol): 事实上的标准域间路由协议
+     - 将Internet “粘合” 为一个整体的关键

+   ◆ BGP为每个AS提供了一种手段:
+     - eBGP: 从邻居AS获取子网可达性信息.
+     - iBGP: 向所有AS内部路由器传播子网可达性信息.
+     - 基于可达性信息与策略，确定到达其他网络的“好”路径.

◆ 允许子网向Internet其余部分通告它的存在:
“我在这里！”