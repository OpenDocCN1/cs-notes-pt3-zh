# 求图的着色数

+   设图 $G=\langle V,E\rangle$，且 $v_i,v_j\in V$ 中不相邻两结点。现引进下面二个符号。

+   $\overline{G}_{ij}$ 表示 $G$ 中加上一条连接 $v_i$ 和 $v_j$ 的边所得到的图。显然 $\overline{G}_{ij}+ (v_i;v_j)$ 相同。

+   $G_{ij}$ 表示把 $v_i$ 和 $v_j$ 两结点收缩为一个结点 $z$ 所得到的图，即图 $G$ 中凡是与 $v_i$ 和 $v_j$ 关联的边都改为与 $z$ 关联。

$$\chi(G)=\min\{\chi(\overline{G}_{ij}),\ \chi(G_{ij})\}。$$