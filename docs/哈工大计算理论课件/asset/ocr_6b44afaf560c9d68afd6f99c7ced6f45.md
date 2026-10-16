# Formal definition of pushdown automata

+   Example 1: PDA for $L = \{0^n1^n \mid n \ge 0\}$
+   $M_1 = (Q, \Sigma, \Gamma, \delta, q_1, F)$
+   where $Q = \{q_1, q_2, q_3, q_4\}$
+   $\Sigma = \{0,1\}$
+   $\Gamma = \{0,\$\}$
+   $F = \{q_1, q_4\}$

Transition function is described in the following (blank stands for Φ)

| input | 0 |  |  | 1 |  |  | ε |  |  |
| stack | 0 | $ | ε | 0 | $ | ε | 0 | $ | ε |
| q1 |  |  |  |  |  |  |  |  | {(q2, $)} |
| q2 |  | {(q2, 0)} |  | {(q3, ε)} |  |  |  |  |  |
| q3 |  |  |  | {(q3, ε)} |  |  |  | {(q4, ε)} |  |
| q4 |  |  |  |  |  |  |  |  |  |