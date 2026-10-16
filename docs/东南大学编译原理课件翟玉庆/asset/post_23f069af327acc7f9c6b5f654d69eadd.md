
## CHAPTER 3 LEXICAL ANALYSIS

### Section 5 Regular Expression to an NFA

**2. Construction of an NFA from a Regular Expression**

**a) Algorithm**

- Input. A regular expression *r* over an alphabet Σ.
- Output. An NFA *N* accepting *L(r)*.

**Method**

1. Parse *r* into its constituent sub-expressions.
2. Use rules in the next pages to construct NFAs for each of the basic symbols in *r* (those that are either ε or an alphabet symbol).
3. Use rules in the next and next page to combine these NFAs inductively, and obtain the NFA for the entire expression.

**Rules**

1. For ε,

   ![img/353f619caa6c5715591f2105bdfa2865_135_0.png](img/353f619caa6c5715591f2105bdfa2865_135_0.png)

2. For a in Σ,

   ![img/353f619caa6c5715591f2105bdfa2865_135_1.png](img/353f619caa6c5715591f2105bdfa2865_135_1.png)

### Section 6 An FA to Regular Expression

**1. Basic Ideas**

Reduce the number of states by merging states.

**2. Algorithm**

- Input: An FA *M*.
- Output: A regular expression *r* over an alphabet Σ that recognizes the same language as FA *M*.

**Method**

- Extend the concept of an FA, and let the arrows be marked by regular expressions.
- Add two nodes x, y to the FA *M*, and get *M′* that recognizes the same regular language.

![](img/353f619caa6c5715591f2105bdfa2865_139_0.png)

- Use the following rules to combine the regular expressions in the FAs inductively, and obtain the entire expression for the FA.

![](img/353f619caa6c5715591f2105bdfa2865_140_0.png)

![](img/353f619caa6c5715591f2105bdfa2865_142_0.png)

### Section 7 Regular Grammar to an NFA

**1. Basic Properties**

- For each regular grammar G=(V_N, V_T, P, S), there is an FA M=(Q, Σ, f, q₀, Z), and L(G)=L(M).
- For each FA M, there is a right-linear grammar and a left-linear grammar that recognize the same language. L(M)=L(G_R)=L(G_L).

**2. Right-Linear Grammar to an FA**

- Input: G=(V_N, V_T, P, S).
- Output: FA M=(Q, Σ, move, q₀, Z).
- Method:
  - Consider each non-terminal symbol in G as a state, and add a new state T as an accepting state.
  - Let Q=V_N ∪ {T}, Σ=V_T, q₀=S; if there is the production S→ε, then Z={S,T}, else Z={T}.
  - For each production, construct the function move.
    - a) For productions similar to A₁ → aA₂, construct move(A₁, a)=A₂.
    - b) For productions similar to A₁ → a, construct move(A₁, a)=T.
    - c) For each a in Σ, move(T, a)=∅; that means the accepting states do not recognize any terminal symbol.

**E.g.** A regular grammar G=({S,A,B},{a,b,c},P,S)

```
P: S → aS | aB
   B → bB | bA
   A → cA | c
```

Construct an FA for the grammar G.

**Answer:** Let M=(Q, Σ, f, q₀, Z).

1. Add a state T, so Q={S,B,A,T}; Σ={a,b,c}; q₀=S; Z={T}.
2. f:

|  |  |
|---|---|
| f(S,a)=S | f(S,a)=B |
| f(B,b)=B | f(B,b)=A |
| f(A,c)=A | f(A,c)=T |

![](img/353f619caa6c5715591f2105bdfa2865_147_0.png)

**3. FA to Right-Linear Grammar**

- Input: M=(S, Σ, f, s₀, Z).
- Output: RG=(V_N, V_T, P, s₀).
- Method:
  - If s₀ ∉ Z, then the productions are:
    - a) For the mapping f(Aᵢ, a)=Aⱼ in M, there is a production Aᵢ → aAⱼ.
    - b) If Aⱼ ∈ Z, then add a new production Aᵢ → a; then we get Aᵢ → a | aAⱼ.
  - If s₀ ∈ Z, then we will get the following productions besides the productions we have gotten based on the former rule:
    - For the mapping f(s₀, ε)=s₀, construct new productions, s₀′ → ε | s₀, and s₀′ is the new starting state.
