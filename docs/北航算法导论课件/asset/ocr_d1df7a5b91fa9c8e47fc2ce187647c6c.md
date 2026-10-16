# 16.1.3 Converting a DP solution to a greedy solution

Theorem 16.1 Let S_ij ≠ ∅, and let a_m be the activity in S_ij with the earliest finish time: f_m = min {f_k : a_k ∈ S_ij}. Then

+   1. a_m is used in some maximum-size subset of mutually compatible activities of S_ij. (a_m包含在某个最大相容活动子集中)

Proof 1. Let A_ij be a maximum-size subset of mutually Compatible activities in S_ij. Order activities in A_ij in monotonically increasing order of finish time. Let a_k be the first activity in A_ij.

+   If a_k = a_m, done (a_m is used in a maximum-size subset).

![](bbox=[0.68, 0.62, 0.98, 0.78])

+   Otherwise, construct B_ij = A_ij - {a_k} ∪ {a_m} (replace a_k by a_m). Activities in B_ij are disjoint. (Activities in A_ij are disjoint, a_k is the first activity in A_ij to finish. f_m ≤ f_k ⇒ a_m doesn’t overlap anything else in B_ij). Since |B_ij| = |A_ij| and A_ij is a maximum-size subset, so is B_ij.