# 2.1.1 Loop invariants and the correctness of insertion sort

+   - three properties hold for insertion sort

Loop invariant: original A[1 .. j-1] is permuted to A'[1 .. j-1] but in sorted order

+   - Initialization: j=2, A[1 .. j-1] consists of just the single A[1], which is the original element in A[1], and is sorted. Obviously, the loop invariant holds prior to the first iteration of the loop.

+   - Maintenance: A'[1 .. j-1] is in sorted order, sorting A[j] into A'[1 .. j-1], s.t. <a'₁, a'₂, ..., a'ₖ, aⱼ, a'ₖ₊₁, ..., ..., a'ⱼ₋₁>, obviously, it is sorted. The second property holds for the outer loop.

+   - Termination: when j=n+1. A'[1 .. j-1] = A'[1 .. n] consists of the elements originally in A[1 .. n], but in sorted sorder. A'[1 .. n] is the entire array! Hence, the algorithm is correct.