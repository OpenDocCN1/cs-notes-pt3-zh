# Circuit Complexity

+   Proof:
+   - The only remaining input is the circuit correspond to the certificate $c$, we call this circuit $C$ and output it
+   - If $C$ is satisfiable, a certificate exists, so w is in $A$
+   - Or, if w is in $A$, a certificate exists, so $C$ is satisfiable
+   - Then we need to show the reduction runs in polynomial time
+   - In the tableau method, the construction of the circuit can be done in time that is polynomial in n
+   - The running time of the verifier is $n^k$ for some $k$
+   - So, the size of the circuit is $O(n^{2k})$
+   - So, the running time of the reduction is $O(n^{2k})$