# 16.1.3 Converting a DP solution to a greedy solution

# Theorem 16.1

Let $S_{ij} \neq \varnothing$, and let $a_m$ be the activity in $S_{ij}$ with the earliest finish time: $f_m = \min \{f_k : a_k \in S_{ij} \}$. Then

+   1. $a_m$ is used in some maximum-size subset of mutually compatible activities of $S_{ij}$. ($a_m$ 包含在某个最大相容活动子集中）

+   2. $S_{im} = \varnothing$, so that choosing $a_m$ leaves $S_{mj}$ as the only nonempty subproblem. (仅剩下一个非空子问题 $S_{mj}$)

# Proof

2. Suppose there is some $a_l \in S_{im}$. Then $f_i \le s_l < f_l \le s_m < f_m \Rightarrow f_l < f_m$. Then $a_l \in S_{ij}$ and it has an earlier finish time than $f_m$, which contradicts our choice of $a_m$. Therefore, there is no $a_l \in S_{im} \Rightarrow S_{im} = \varnothing$.