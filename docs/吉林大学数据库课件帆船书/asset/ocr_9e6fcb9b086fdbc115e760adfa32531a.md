# Semijoin Strategy

+   - Let $r_1$ be a relation with schema $R_1$ stores at site $S_1$
+     Let $r_2$ be a relation with schema $R_2$ stores at site $S_2$
+   - Evaluate the expression $r_1 \bowtie r_2$ and obtain the result at $S_1$.
+     1. Compute $temp_1 \leftarrow \prod_{R1 \cap R2} (r1)$ at S1.
+   - 2. Ship $temp_1$ from $S_1$ to $S_2$.
+   - 3. Compute $temp_2 \leftarrow r_2 \bowtie temp1$ at $S_2$
+   - 4. Ship $temp_2$ from $S_2$ to $S_1$.
+   - 5. Compute $r_1 \bowtie temp_2$ at $S_1$. This is the same as $r_1 \bowtie r_2$.

![](bbox=[0.0, 0.0, 0.09, 0.13])