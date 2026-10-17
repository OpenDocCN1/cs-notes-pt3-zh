# # Testing for BCNF(cont.)

However, using only F to test for BCNF may be incorrect when testing a relation in a decomposition of R.

+   E.g. Consider \( R(A, B, C, D) \), with \( F={A \rightarrow B, B \rightarrow C} \)

+   R is in BCNF ? Which is candidate key?

+   Decompose \( R \) into \( R_1(A,B) \) and \( R_2(A,C,D) \)

+   Neither of the functional dependencies in \( F \) contain only attributes from \( (A,C,D) \), so no FD violates BCNF, we might be mislead into thinking \( R_2 \) satisfies BCNF.

+   In fact, dependency \( A \rightarrow C \) in \( F^+ \) shows \( R_2 \) is not in BCNF.

(可在F下判别R是否违反BCNF，但须在F+下判别R的分解式是否违反BCNF.)