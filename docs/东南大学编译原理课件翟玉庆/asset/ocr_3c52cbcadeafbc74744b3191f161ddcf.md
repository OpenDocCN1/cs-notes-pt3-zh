# CHAPTER 3 LEXICAL ANALYSIS

# Section 7 Regular Grammar to an NFA

2、 Right-linear grammar to FA

+   - Input : G=(V_N, V_T, P, S)

+   - Output : FA M=(Q, Σ, move, q₀, Z)

+   - Method :

+   - Consider each non-terminal symbol in G as a state, and add a new state T as an accepting state.

+   - Let Q=V_N ∪ {T} , Σ = V_T , q₀ =S; if there is the production S→ ε , then Z={S,T}, else Z={T} ;