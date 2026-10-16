

## 11.3 树遍历

![](img/c25dfd82fc242c2db53bc942dcad6885_1869_0.png)

- a）前序：a,b,e,j,k,n,o,p,f,c,d,g,l,m,h,i
- b）中序：j,e,n,k,o,p,b,f,a,c,l,g,m,d,h,i
- c）后序：j,n,o,p,k,e,f,b,c,l,m,g,h,i,d,a

## 中缀、前缀和后缀表示法

表示 ((x+y)^2+((x-4)/3)) 的二叉树

![](img/c25dfd82fc242c2db53bc942dcad6885_1870_0.png)

- a ) 前缀：+ ^ + x y 2 / - x 4 3
- b ) 中缀：(x+y)^2 + (x-4)/3
- c ) 后缀：x y + 2 ^ x 4 - 3 / +

## 前缀（波兰式）
（前缀表达式（波兰式））

- 无歧义且无需括号
- 从左到右 F x y
- 运算符符号在参数之前

1. x - 64 + 5 ÷ 22
2. × 2 + 5 ÷ 22 因为正确类型的第一个串是 - 64 且 6 - 4 = 2
3. × 2 + 5 1 用 2 ÷ 2 或 1 替换 ÷ 22
4. × 2 6 用 5 + 1 或 6 替换 + 5 1
5. 12 用 2 × 6 替换 × 2 6

## 中缀表示法（中缀表示法）

- 存在歧义

![](img/c25dfd82fc242c2db53bc942dcad6885_1872_0.png)

## 后缀（后缀表达式）

![](img/c25dfd82fc242c2db53bc942dcad6885_1873_0.png)

- ab-cde/+*
- a=2,b=1,c=3

(a)

Figure 7.14

## 搜索一般树

- 定义 B(T)

## 定义二元位置树 B(T) :

- 如果 v 在 A 中，则 v 在 B(T) 中的左子代 V_L 是 v 在 T 中的第一个子代，如果存在。
- v 在 B(T) 中的右子代 V_R 是 v 在 T 中的下一个兄弟，如果存在。

## 搜索一般树

![](img/c25dfd82fc242c2db53bc942dcad6885_1876_0.png)

![](img/c25dfd82fc242c2db53bc942dcad6885_1876_1.png)

Figure 7.15

## T 的链表表示

![](img/c25dfd82fc242c2db53bc942dcad6885_1877_0.png)

T

(a)

![](img/c25dfd82fc242c2db53bc942dcad6885_1877_1.png)

B(T)

(b)

| INDEX | LEFT | DATA | RIGHT |
|---|---|---|---|
| 1 | 2 | ✗ | 0 |
| 2 | 3 | a | 0 |
| 3 | 6 | b | 4 |
| 4 | 0 | c | 5 |
| 5 | 0 | d | 0 |
| 6 | 0 | e | 7 |
| 7 | 0 | f | 8 |
| 8 | 0 | g | 0 |

(c)

Figure 7.16

## 伪代码版本

```
SUBROUTINE INORDER(T,v)
1. IF (v_L exists) THEN
   a. CALL INORDER(T(v_L), v_L)
2. CALL VISIT(v)
3. IF (v_R exists) THEN
   a. CALL INORDER(T(v_R), v_R)
4. RETURN
END OF SUBROUTINE INORDER
```

## 伪代码版本

```
SUBROUTINE POSTORDER(T ,v)
1. IF (v_L exists) THEN
   a. CALL POSTORDER(T (v_L), v_L)
2. IF (v_R exists) THEN
   a. CALL POSTORDER(T (v_R), v_R)
3. CALL VISIT(v)
4. RETURN
END OF SUBROUTINE POSTORDER
```

![](img/c25dfd82fc242c2db53bc942dcad6885_1881_0.png)

- a) 前序: a, b, d, g, e, h, i, c, f
- b) 中序: g, d, b, h, e, i, a, c, f
- c) 后序: g, d, h, i, e, b, f, c, a

## 二元树的遍历问题的应用

公式的三种表示方法：

- 1. 中缀表示法
- 2. 前缀表示法
  波兰表示法
- 3. 后缀表示法
  逆波兰表示法

## 11.4 生成树 （生成树）

- 设 G 为简单图。G 的生成树是 G 的子图，该子图是包含 G 的每个顶点的树。
  - T 是与 G 具有完全相同顶点的树
  - T 可以通过删除 G 的某些边从 G 得到。

## Example 3

- 生成树不是唯一的。

![](img/c25dfd82fc242c2db53bc942dcad6885_1884_0.png)

定义 G 的生成树：G 的是一棵树的生成子图。

树枝：生成树 T 中的边；

弦：G 的不在生成树中的边；

生成树 T 的补：所有弦的集合。

定理 连通图至少有一棵生成树。

## 一个连通图可有多棵生成树。

![](img/c25dfd82fc242c2db53bc942dcad6885_1886_0.png)

充分性：若G是连通的，

- (1) 若G无回路，则G本身是树，即生成树。
- (2) 若存在回路，去掉回路中任一辺，不影响连通性，也不减少顶点。

所有回路都移去一条边，剩下的子图包含所有顶点，又是无回路的连通图，即为生成树。

注： ① 移去边时可随意，故生成树不唯一。

② 生成树是G的最小连通生成子图，若将G =（V，E）看成是各顶点间的通讯联络图，则生成树T =（V，E’）即为各顶点间直接或间接联络的最小通讯联络图。

## IP 组播

- 目前，使用得最为广泛的组播技术是IP Multicast。IP组播技术是一种为优化使用网络资源而产生的技术，通常用于多点工作方式下的应用程序中，它是标准IP网络层协议技术的一个扩展。

从Steve Deering于1989年提出的IETF的RFC1112"Host Extension for IP Multicast"中的定义我们可以得知：IP组播的核心思想是--通过一个IP地址向一组主机发送数据（UDP包）。发送者仅仅向一个组地址发送信息，接收者只需加入到这个分组就可以接收信息，所有的接收者接收的是同一个数据流，组中成员是动态的，可以根据自己的意愿随时随意加入或退出。每 一台主机都可以同时加入到多个组中，每一个组播地址可以在不同的端口或者不同的套接字（Socket）上有多个数据流，同时许多实际应用可以共享一个组地址。IP组播技术可以有效地避免重复发送可能引起的广播风暴，并且能够突破路由器的限制，将数据包传送到其它网段。

