# Regular expressions

+   - $R = \varepsilon$. Then $L(R) = \{ \varepsilon \}$, and the following NFA recognizes $L(R)$
+     - $N = (\{q_1\}, \Sigma, \varepsilon, q_1, \{q_1\})$, where $\delta(r,b)=\Phi$ for any $r$ and $b$.
+   - $R = \Phi$. Then $L(R) = \Phi$, and the following NFA recognizes $L(R)$.
+     - $N = (\{q_1\}, \Sigma, \varepsilon, q_1, \Phi)$, where $\delta(r,b)=\Phi$ for any $r$ and $b$.
+   - $R = (R_1 \cup R_2)$,
+   - $R = (R_1 \circ R_2)$,
+   - $R = R_1 *$,
+     - We can prove by construction as we have done in the proofs of closure.

+   - By the definition of regular language, we can get NFA → A.
+   - We finish the proof.