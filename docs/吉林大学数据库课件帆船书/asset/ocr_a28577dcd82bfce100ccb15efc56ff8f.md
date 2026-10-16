# Estimation of the Size of Joins (Cont.)

+   - If \(R \cap S = \{A\}\) is not a key for \(R\) or \(S\).
+     If we assume that every tuple \(t\) in \(R\) produces tuples in \(R \bowtie S\), the number of tuples in \(R \bowtie S\) is estimated to be:
+   
+     \[
+     \frac{n_r \ast n_s}{V(A,s)}
+     \]
+   
+     If the reverse is true, the estimate obtained will be:
+   
+     \[
+     \frac{n_r \ast n_s}{V(A,r)}
+     \]
+   
+     The lower of these two estimates is probably the more accurate one.

+   - Can improve on above if histograms are available
+     - Use formula similar to above, for each cell of histograms on the two relations