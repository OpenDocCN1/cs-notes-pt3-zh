# Equivalence of NFAs and DFAs

Consider the case where N has no ε arrow.

+   - Q' = P(Q)

+   - δ'(R, a) = { q ∈ Q | q ∈ δ(r, a) for some r ∈ R }
+     = δ'(R, a) = ∪_{r∈R} δ(r, a)

+   - R is a state of M, it is also a set of states of N.

+   - When M reads a symbol a in state R, it shows where a takes each state in R.

+   - Because each state may go to a set of states, we take the union of all these sets.

+   - q₀' = {q₀}

+   - F' = { R ∈ Q' | R contains an accept state of N }