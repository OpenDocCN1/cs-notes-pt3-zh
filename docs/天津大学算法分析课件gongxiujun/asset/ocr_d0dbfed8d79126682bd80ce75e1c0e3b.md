# # Properties of A-star

In practice, how to estimate h(x) to its real value h*(x) is a hard point

+   - Admissibility: the heuristic function h(x) is admissible, meaning that it never overestimates the actual minimal cost of reaching the goal.

+   - Monotonicity (Consistency): the heuristic function h(x) is monotonic, means that for any pair of adjacent nodes x and y, h(x) ≤ h(y) + d(x, y)