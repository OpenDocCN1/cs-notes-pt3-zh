# Example continued

+   - Let 3∈S, and let x+y∈S if x,y∈S. Let A = {n∈Z⁺ | (3|n)}.

+   - **Theorem:** A=S. **Proof:** We show that A⊆S and S⊆A.

+   - To show A⊆S, show [n∈Z⁺ ∧ (3|n)]→ n∈S.

+   - **Inductive proof.** Let P(n):≡ n∈S. Induction over positive multiples of 3. Base case: n=3, thus 3∈S by def’n. of S. Inductive step: Given P(n), prove P(n+3). By inductive hyp., n∈S, and 3∈S, so by def’n of S, n+3∈S.

+   - To show S⊆A: let n∈S, show n∈A.

+   - **Structural inductive proof.** Let P(n):≡n∈A. Two cases: n=3 (base case), which is in A, or n=x+y (recursive step). We know x and y are positive, since neither rule generates negative numbers. So, x<n and y<n, and so we know x and y are in A, by strong inductive hypothesis. Since 3|x and 3|y, we have 3|(x+y), thus x+y ∈ A.