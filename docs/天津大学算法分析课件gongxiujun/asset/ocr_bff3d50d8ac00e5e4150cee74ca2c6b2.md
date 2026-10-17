# # Problem statements

+   - **Branch & Bound (BB)** is an enhancement of backtracking for searching solution space with bounding, respect to a global optimization problem(min/max, for simplicity, just consider the min problem)

where \(x=(x_1, x_2, \cdots, x_n)\), \(x \in S_i\), \(S = S_1 \cup S_2, \cdots, \cup S_n\), and each \(S_i\) is a limited set. Usually , \(x\) is constrained with

\(g(x) < b\) (2)

+   - It consists of systematic enumeration of all candidate solutions, discarding large subsets of fruitless candidates by using **upper** and **lower** estimated bounds of quantity being optimized