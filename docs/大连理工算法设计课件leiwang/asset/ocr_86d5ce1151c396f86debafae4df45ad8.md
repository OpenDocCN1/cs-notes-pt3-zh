# # Set definition of O-notation

O(g(n)) = { f(n) : there exist constants c > 0, n₀ > 0 such that 0 ≤ f(n) ≤ cg(n) for all n ≥ n₀ }

**EXAMPLE:** 2n² ∈ O(n³)

(Logicians: λn.2n² ∈ O(λn.n³), but it’s convenient to be sloppy, as long as we understand what’s *really* going on.)