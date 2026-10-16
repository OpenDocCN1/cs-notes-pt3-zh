# 16.1.1 Optimal substructure of activity selection

# Space of subproblems

+   - $S_{ij} = \{a_k \in S : f_i \le s_k < f_k \le s_j\}$

+   - Assume that activities are sorted by monotonically increasing finish time （以结束时间单调增的方式对活动进行排序）

$f_0 \le f_1 \le f_2 \le \cdots \le f_n < f_{n+1}$ (if $i \le j$, then $f_i \le f_j$) (16.1)

![](bbox=[0.05, 0.6, 0.95, 0.92])