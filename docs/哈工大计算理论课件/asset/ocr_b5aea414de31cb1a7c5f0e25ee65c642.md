# Circuit Complexity

+   - Proof Idea:
+     - We modify M so that the input is encoded into {0,1}
+     - When M is about to accept, it moves its head onto the leftmost tape cell and writes the blank symbol on that cell prior to entering the accept state
+     - Then, we can designate a gate in the final row of the circuit to be the output gate