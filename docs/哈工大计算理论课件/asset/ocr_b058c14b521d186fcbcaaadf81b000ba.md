# Formal definition of pushdown automata

+   - Definition
+   - A pushdown automaton is a 6-tuple $(Q,\Sigma,\Gamma,\delta,q_0,F)$ where $Q,\Sigma,\Gamma$ and $F$ are all finite sets, and
+     - $Q$ is the set of states,
+     - $\Sigma$ is the input alphabet,
+     - $\Gamma$ is the stack alphabet,
+     - $\delta: Q \times \Sigma_\varepsilon \times \Gamma_\varepsilon \to P(Q \times \Gamma_\varepsilon)$ is the transition funtion,
+     - $q_0$ is the start state, and
+     - $F \subseteq Q$ is the set of accept states.