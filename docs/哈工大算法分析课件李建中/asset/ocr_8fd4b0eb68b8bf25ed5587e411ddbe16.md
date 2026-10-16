# 加权Matroid上Greedy 算法
Matroid的优化问题
实例背景：
据已有用Greedy算法能解决的最小生成树问题可推广到加权Matroid中寻找优化问题。给定Matroid M=(S,I)及其中权重W，我们按某种顺序A∈I，使得W(A)最大。

# 实例/最大生成树问题
一问题定义
输入：无向图G=(V,E)，权重函数W:E→正整数集
输出：边集A⊆E，G(V,A)是森林，W(A)最大
一最大生成树加权Matroid上优化问题
一构造：
M₀=(S₀,I₀), S₀=E, I₀={A⊆E, G(V,A)是森林}，M₀是森林
M₀的权重函数W₀：
W(A)最大

# 实例2：最小生成树问题
一问题定义
输入：无向图G=(V,E)，权重函数W:E→正整数集
输出：边集A⊆E，G(V,A)是森林，W(A)最小
一最小生成树加权Matroid上优化问题
构造：
M₀=(S₀,I₀), S₀=E, I₀={A⊆E, G(V,A)是森林}，M₀是森林
构造权重函数W₀：
W₀(x)=W(x), W₀≥max{W(x)}
W₀(A)=W(A)
W₀(A)=W(A), ∀x∈E
M₀被赋予W(A)最小：
(V,A)连通
W(A)最小, 有|V|-1条边。

# 加权Matroid优化问题的定义
输入：Matroid M=(S,I)，权重W:S→正整数集
输出：M的独立集A∈I，使得W(A)最大

# 算法
Greedy(M,W)
1 A=Φ;
2 按W值递减排序S;
3 For ∀x∈S (按W(x)递减顺序) DO
4 If A∪{x}∈I /* 保持者W(x)最大取x */
5 Then A=A∪{x};
6 Return A.
时间复杂
step 2: O(|S|log|S|)
step 4: O(f(|S|))
T(|S|)=O(|S|log|S|+|S|f(|S|))

# 优化性质
定义1: 设x是一个被Greedy算法中丢弃元素，也含x的集合A是A包含可换成M'=(S',I')的独立集S'=A-{x}, M'=(S',I')定义如下：
I'={B⊆S' | B∪{x}∈I}
则M'的每个独立集M的独立集构成一个组。
证：因为A-{x}∈I, 称A-{x}∈I'。
A' =A∪M'的独立集，则M'的每个独立集B满足W(B)>W(A')。
由子B∪{x}∈I, W(A)=W(A')+W(x),
W(B∪{x})=W(B)+W(x)>W(A')+W(x)=W(A),
故A优化错误。