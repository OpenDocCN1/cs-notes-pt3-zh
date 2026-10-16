# Exponential Space Completeness

# Proof:

+   - A string may fail to be rejecting computation history if
+     - Fail to start
+     - Fail to end
+     - Incorrect some where in the middle

+   - So, expression $R_2 = R_{\text{bad-start}} \cup R_{\text{bad-window}} \cup R_{\text{bad-reject}}$

+   - We construct expression $R_{\text{bad-start}}$ to generate all strings that fail to start with the start configuration $C_1$ of $M$ on $w$

+   - $C_1$ looks like $q_0 w_1 w_2 \dots w_n \sqcup \sqcup \#$

+   - We write $R_{\text{bad-start}}$ as the union of several subexpression to handle each part of $C_1$ :

$R_{\text{bad-start}} = S_0 \cup S_1 \cup \dots \cup S_n \cup S_b \cup S_\#$