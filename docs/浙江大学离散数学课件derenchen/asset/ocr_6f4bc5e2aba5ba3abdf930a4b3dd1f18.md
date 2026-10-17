# 二、关系的表达方式

1. **集合表达式**：列出关系中的所有有序对。

**例7.4** 设 $A=\{1,2,3,4\}$，试列出下列关系 $R$ 的元素。

+   (1) $R=\{\langle x,y\rangle\mid x\text{ 是 }y\text{ 的倍数}\}$  
+   (2) $R=\{\langle x,y\rangle\mid (x-y)^2\in A\}$  
+   (3) $R=\{\langle x,y\rangle\mid x/y\text{ 是素数}\}$  
+   (4) $R=\{\langle x,y\rangle\mid x\ne y\}$  
+   (5) $R=\{\langle x,y\rangle\mid (x,y\in A)\land(x<y)\}$

**解：** (1) $R=\{\langle4,4\rangle,\langle4,2\rangle,\langle4,1\rangle,\langle3,3\rangle,\langle3,1\rangle,\langle2,2\rangle,\langle2,1\rangle,\langle1,1\rangle\}$

(2) $R=\{\langle2,1\rangle,\langle3,2\rangle,\langle4,3\rangle,\langle3,1\rangle,\langle4,2\rangle,\langle2,4\rangle,\langle1,3\rangle,\langle3,4\rangle,\langle2,3\rangle,\langle1,2\rangle\}$

(3) $R=\{\langle2,1\rangle,\langle3,1\rangle,\langle4,2\rangle\}$

(4) $R=E_A-I_A=\{\langle1,2\rangle,\langle1,3\rangle,\langle1,4\rangle,\langle2,1\rangle,\langle2,3\rangle,\langle2,4\rangle,$  
$\langle3,1\rangle,\langle3,2\rangle,\langle3,4\rangle,\langle4,1\rangle,\langle4,2\rangle,\langle4,3\rangle\}$

(5) $R=\{\langle1,2\rangle,\langle1,3\rangle,\langle1,4\rangle,\langle2,3\rangle,\langle2,4\rangle,\langle3,4\rangle\}$