# 构造 a-4+c 的语法树：

+   1. `p1:=mkleaf(id,entry a);`
+   2. `p2:=mkleaf(num, 4);`
+   3. `p3:=mknode('-', p1,p2)`
+   4. `p4:=mkleaf(id, entry c)`
+   5. `p5:=mknode('+',p3,p4)`

![](bbox=[0.032, 0.343, 0.478, 0.876])