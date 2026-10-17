# Showing each is a subset of the others

℘(A ∩ B)^c = A^c ∪ B^c

Proof) Want to prove that (A ∩ B)^c ⊆ A^c ∪ B^c and (A ∩ B)^c ⊇ A^c ∪ B^c

x ∈ (A ∩ B)^c
⇒ x ∉ (A ∩ B)
⇒ ¬ (x ∈ A ∩ B)
⇒ ¬ (x ∈ A ∧ x ∈ B)
⇒ ¬ (x ∈ A) ∨ ¬ (x ∈ B)
⇒ x ∉ A ∨ x ∉ B
⇒ x ∈ A^c ∨ x ∈ B^c
⇒ x ∈ A^c ∪ B^c