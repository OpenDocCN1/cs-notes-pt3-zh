# 7.4 Bézier 曲面

# 7.4.1 Bézier 曲面的定义

Bézier 曲面是 Bézier 曲线向曲面的直接推广。给定三维空间 $(m+1)\times(n+1)$ 个点 $P_{ij}(x_{ij}, y_{ij}, z_{ij})$, $i=0,1,\cdots,m$; $j=0,1,\cdots,n$，张量积形式的参数多项式曲面：

$P(u,v)=\sum_{i=0}^{m}\sum_{j=0}^{n}P_{ij}B_{i,m}(u)B_{j,n}(v),\;0\le u,\;v\le1$

称为 $m\times n$ 次 Bézier 曲面。$P_{ij}$ 称为 $P(u,v)$ 的控制顶点，由两组多边形 $P_{i0},P_{i1},\cdots,P_{in}$ $(i=0,1,\cdots,m)$ $P_{0j},P_{1j},\cdots,P_{mj}$ $(j=0,1,\cdots,n)$ 组成的网格叫做 $P(u,v)$ 的控制网格，$B_{i,m}(u)$ 和 $B_{j,n}(v)$ 分别为