# Induction and Recursively Defined Sets

Example: Show that the set S defined by specifying that 3 ∈ S and that if x ∈ S and y ∈ S, then x + y is in S, is the set of all positive integers that are multiples of 3.

Solution: Let A be the set of all positive integers divisible by 3. To prove that A = S, show that A is a subset of S and S is a subset of A.

+   - A ⊆ S: Let P(n) be the statement that 3n belongs to S.
+     BASIS STEP: 3·1 = 3 ∈ S, by the first part of recursive definition.
+     INDUCTIVE STEP: Assume P(k) is true. By the second part of the recursive definition, if 3k ∈ S, then since 3 ∈ S, 3k + 3 = 3(k + 1) ∈ S. Hence, P(k + 1) is true.

+   - S ⊆ A:
+     BASIS STEP: 3 ∈ S by the first part of recursive definition, and 3 = 3·1.
+     INDUCTIVE STEP: The second part of the recursive definition adds x + y to S, if both x and y are in S. If x and y are both in A, then both x and y are divisible by 3. By part (i) of Theorem 1 of Section 4.1, it follows that x + y is divisible by 3.

+   - We used mathematical induction to prove a result about a recursively defined set. Next we study a more direct form induction for proving results about recursively defined sets.