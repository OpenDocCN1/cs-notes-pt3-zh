
## Time Hierarchy Theorem
- We organize D’s single tape into tracks
  - We store content of the first track in the odd positions and content of the second track in the even positions
  - Alternatively, we may have this effect by enlarging D’s tape alphabet to include each pair of symbols, one from the first track, one from the other
  - This could be extended to multiple tracks, with more than 2 tracks
  - This only introduce a constant factor overhead in time
  - *D has 3 tracks*

- At stages 3 and 4, *D* must decrement the step counter
  - *D* can do so without adding to much time to the simulation by keeping the counter in binary on a **third track**
  - And, moving it to keep it near the present head position
  - The magnitude of the count is about *t(n)/log t(n)*, so its length is log (*t(n)/log t(n)*) = *O(log t(n))*
  - So, it adds *O(log t(n))* to the simulation
  - Totally, the simulation running time is *O(t(n))*.
  - So, A is decidable in time *O(t(n))*

- Is it A not decidable in $o(t(n)/\log t(n))$ ?
  - Assume contrary that TM $M$ decides $A$ in time $g(n)$, where $g(n)$ is $o(t(n)/\log t(n))$.
  - $D$ can simulate $M$ using time $dg(n)$ for some constant $d$
  - If the total simulation time is at most $t(n)/\log t(n)$, simulation will run to completion (without counting the counter updating)
  - Some constant $n_0$ exists, where $dg(n) < t(n)/\log t(n)$ for all $n \ge n_0$.
  - So, $D$’s simulation of $M$ will run to completion so long as the input has length $n_0$ or more

- Is it A not decidable in $o(t(n)/\log t(n))$ ?
  - When $D$ is run on input $\langle M\rangle 10^{n_0}$. This input is longer than $n_0$, so simulation in stage 4 will complete
  - Therefore, $D$ will do the opposite of $M$ on the same input
  - Hence, $M$ does not decide $A$, which contradicts our assumption
  - So, $A$ is not decidable in $o(t(n)/\log t(n))$ time

- Corollary
  - For any two functions $t_1, t_2 : N \to N$, where $t_1(n)$ is $o(t_2(n)/\log t_2(n))$ and $t_2$ is space constructible,
    $$\text{TIME}(t_1(n)) \subset \text{TIME}(t_2(n))$$

- Corollary
  - This is also true for real numbers $c_1$ and $c_2$
    $$\text{TIME}(t_1(n^{c_1})) \subset \text{TIME}(t_2(n^{c_2}))$$

- Corollary
  $$\text{P} \subset \text{EXPTIME}$$

## Exponential Space Completeness
- We use previous results to demonstrate that a specific language is actually intractable.
  - The hierarchy theorems tell us that a TM can decide more languages in EXPSPACE than it can in PSPACE
  - Then, we show that a particular language concerning generalized regular expressions is complete for EXPSPACE and hence can not be decided in polynomial time or even in polynomial space

- Recall that regular expressions are built up from the atomic expressions φ, ε and members of the alphabet, by using regular operations union (∪), concatenation (o) and star (*)
- Recall that we can test the equivalence of two regular expressions in polynomial space
- Now, we add one more operation. Let ↑ be the exponentiation operation.
- If R is a regular expression and k is a nonnegative integer, writing R ↑ k is equivalent to the concatenation of R with itself k times, in shorthand R^k

- Definition
A language B is EXPSPACE-complete if
  - $B \in \text{EXPSPACE}$
  - Every $A$ in EXPSPACE is polynomial time reducible to $B$

- Theorem
  - $EQ_{\text{REX}\uparrow}$ is EXPSPACE-complete
- Proof Idea:
  - When measuring the complexity of deciding $EQ_{\text{REX}\uparrow}$, we assume that all exponents are written as binary integers
    - The length of an expression is the total number of symbols in it
  - To test whether two expressions with exponentiation are equivalent, we first use repetition to eliminate exponentiation, then we convert the resulting expression to NFAs
  - Then, we use an NFA equivalence testing procedure similar to the one used for deciding the complement of $ALL_{\text{NFA}}$
