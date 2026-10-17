# MIPS特色—非对齐访存指令

+   - 边界不对齐的数据传送（小尾端）

初始值
M[100]
3 2 1 0
A V E

M[104]
D

R2
J O H N

执行 “LWR R2, 0x101”后
R2
J A V E

执行 “LWL R2, 0x104”后
R2
D A V E

初始值
M[200]
3 2 1 0
E

M[204]
D A V

R2
J O H N

执行 “LWR R2, 0x203”后
R2
J O H E

执行 “LWL R2, 0x206”后
R2
D A V E