# 文件分发：客户机/服务器

+   服务器串行地发送N个副本
+     时间： NF/u_s
+   客户机需要F/d_i时间下载

Time to distribute F to N clients using = d_cs = max { NF/u_s, F/min_i(d_i) } client/server approach

increases linearly in N (for large N)

![](bbox=[0.7, 0.25, 0.97, 0.65])