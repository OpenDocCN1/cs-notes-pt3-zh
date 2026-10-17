# Example

Assume: ¬(P→Q)∨(R→P)

+   □ Eliminate ↔, →
+   
+   ¬(¬P ∨ Q)∨(¬R ∨ P)

+   □ Reduce the scope of ¬ through DeMorgan Laws and double negation
+   
+   (P ∧ ¬Q)∨(¬R ∨ P)

+   □ Convert to CNF using the distributive laws and laws for flatten
+   
+   (P ∨ ¬R) ∧ (¬Q ∨ ¬R ∨ P)

+   □ Convert to CCNF by supplementing missing literals
+   
+   (P∨¬R∨Q) ∧ (P∨¬R∨¬Q) ∧ (¬Q∨¬R∨P)