# Regular expressions

+   - The formal definition of computation of GNFA
+     - A GNFA accepts a string *w in* Σ* if *w = w₁ w₂ … wₙ*, where each *wᵢ is in* Σ* a sequence of states *q₀, q₁, … qₖ* exists such that
+       1. *q₀ = q_start* is the start state.
+       2. *qₖ = q_accept* is the accept state
+       3. For each *i*, we have *wᵢ ∈ L(Rᵢ)*, where *Rᵢ = δ̂(qᵢ₋₁, qᵢ)*; in other words, *Rᵢ* is the expression on the arrow from *qᵢ₋₁* to *qᵢ*.