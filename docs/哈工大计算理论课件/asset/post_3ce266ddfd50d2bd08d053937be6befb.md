
## Definition of NP-completeness

- Proof:
- It is obvious that $SAT \in \mathbf{NP}$.
- Suppose $A$ is a language that belongs to $\mathbf{NP}$. Let $N$ be a nondeterministic Turing machine that decides $A$ in $n^k$ time (suppose in form of $n^k$-3 for some constant $k$.
- A tableau for $N$ on $w$ is an $n^k \times n^k$ table whose rows are the configurations of a branch of the computation of $N$ on input $w$.

Tableau

![](img/505b35cb28b35d38fc29ccba74c23087_593_0.png)

start configuration

second configuration

window

cells

n^kth configuration

- For convenience we assume that each configuration starts and ends with a # symbol.
- A tableau is accepting if any row of the tableau is an accepting configuration.

- Construct the reduction $f$ which produces a formula $\phi$.
- Suppose $Q$ and $\Gamma$ are the state and tape alphabet of $N$.
- Let $C = Q \cup \Gamma \cup \{\#\}$, for each $i$ and $j$ between 1 and $n^k$ and for each $s$ in $C$ we have a variable, $x_{i,j,s}$.
- Demonstrate the cell in row $i$ and column $j$ as $cell\ [i,j]$.

- We know that every cell contains a symbol from C. we represent the contents of the cells with the variables of φ. If x_{i,j,s} takes on the value 1, it means that the content of cell [i,j] should be s.

- Now design φ. φ Should satisfy the AND of the four parts φ_cell ∧ φ_start ∧ φ_move ∧ φ_accept.
- φ_cell is defined as:

φ_cell = ∧_{1≤i,j≤n^k} [ (∨_{s∈C} x_{i,j,s}) ∧ (∧_{s,t∈C, s≠t} ¬x_{i,j,s} ∨ ¬x_{i,j,t}) ]

- We can see that φ_cell contains a fragment for each cell in the tableau because i and j range from 1 to n^k.

- Now design φ . φ Should satisfy the AND of the four parts φ_cell ∧ φ_start ∧ φ_move ∧ φ_accept .
- φ_cell is defined as:

```
φ_cell = ∧_{1≤i,j≤n^k} [ (∨_{s∈C} x_{i,j,s}) ∧ (∧_{s,t∈C \ s≠t} (¬x_{i,j,s} ∨ ¬x_{i,j,t})) ]
```

This part constrains that at least one variable is turned on in the corresponding cell.

This part constrains that no more than one variable is turned on in the corresponding

So any assignment to the variables that satisfies must have exactly one variable on for every cell.

- φ_start has to ensures that the first row of the table is the string configuration of N on string w. It is defined as:

φ_start = x_{1,1,#} ∧ x_{1,2,q0} ∧ x_{1,3,w1} ∧ x_{1,4,w2} ∧ ... ∧ x_{1,n+2,w_n} ∧

x_{1,n+3,⊢} ∧ ... ∧ x_{1,n^k-1,⊢} ∧ x_{1,n^k,#}

- φ_accept has to guarantee that an accepting configuration occurs in the tableau. w. It is defined as:

φ_accept = ⋁_{1≤i,j≤n^k} x_{i,j,q_accept}

- φ_move guarantees that each row of the table corresponds to a configuration that legally follows the preceding row’s configuration according to N’s rules.
- If each 2×3 window of cells is legal, then the configuration is legal.

![](img/505b35cb28b35d38fc29ccba74c23087_603_0.png)

![](img/505b35cb28b35d38fc29ccba74c23087_603_1.png)

![](img/505b35cb28b35d38fc29ccba74c23087_603_2.png)

δ(q₁,b)=((q₂,c,L))

δ(q₁,b)=((q₂,a,R))

δ(q₁,a)=((q₁,b,R))

![](img/505b35cb28b35d38fc29ccba74c23087_604_0.png)

![](img/505b35cb28b35d38fc29ccba74c23087_604_1.png)

![](img/505b35cb28b35d38fc29ccba74c23087_604_2.png)

![](img/505b35cb28b35d38fc29ccba74c23087_604_3.png)

![](img/505b35cb28b35d38fc29ccba74c23087_604_4.png)

![](img/505b35cb28b35d38fc29ccba74c23087_604_5.png)

Legal as the two rows are the same

δ(q₁,b)=((q₂,c,L))

δ(q₁,b)=((q₂,c,L))

Example of illegal for N:

![](img/505b35cb28b35d38fc29ccba74c23087_605_0.png)

![](img/505b35cb28b35d38fc29ccba74c23087_605_1.png)

![](img/505b35cb28b35d38fc29ccba74c23087_605_2.png)
