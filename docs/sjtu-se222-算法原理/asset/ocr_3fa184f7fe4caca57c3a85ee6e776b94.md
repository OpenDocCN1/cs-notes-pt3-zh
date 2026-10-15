# Subset sum problem

Problem: SubsetSum
Input: A set of numbers A={a₁,a₂,...,aₙ}, and a sum s
Output: Yes, if there exists a subset B ⊆ A such that the sum of B equals to s; No, otherwise.

L[i,j]: Does there exists a subset B of {a₁,...,aᵢ} such that the sum of B equals to j

L[i,j] = { 0 if i = 0
1 if j = 0
L[i-1,j] if i > 0, j > 0, j < aᵢ
L[i-1,j-aᵢ] ∨ L[i-1,j] if i > 0, j > 0, j ≥ aᵢ }

Solution: L[n,s]