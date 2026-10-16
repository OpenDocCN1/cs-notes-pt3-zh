# 图灵机的计算(续)

**计算：** 一个有穷的或无穷的格局序列，序列中的每一个格局都是前一个格局的后继。

$\forall w\in\Sigma^*$，$M$ 从 $\sigma_0=q_0w$ 开始的计算有3种可能：

+   1. 停机在接受格局，即计算为 $\sigma_0,\sigma_1,\ldots,\sigma_n$，其中 $\sigma_n$ 是接受的停机格局；
+   2. 停机在非接受格局，即计算为 $\sigma_0,\sigma_1,\ldots,\sigma_n$，其中 $\sigma_n$ 是非接受的停机格局；
+   3. 永不停机，即计算为 $\sigma_0,\sigma_1,\ldots,\sigma_n,\ldots$