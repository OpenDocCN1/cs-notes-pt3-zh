# OSPF优点(RIP不具备)

+   安全(security): 所有OSPF报文可以被认证
+   (预防恶意入侵)

+   允许使用多条相同费用的路径 (RIP只能选一条)

+   对于每条链路，可以针对不同的TOS设置多个不同的费用度量 (e.g., 卫星链路可以针对“尽力”(best effort) ToS设置“低”费用；针对实时ToS设置“高”费用)

+   集成单播路由与多播路由：
+   - 多播OSPF协议(MOSPF) 与OSPF利用相同的网络拓扑数据

+   OSPF支持对大规模AS分层(hierarchical)