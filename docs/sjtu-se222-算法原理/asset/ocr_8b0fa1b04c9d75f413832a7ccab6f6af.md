# Proof of correctness

Lemma (Invariants)
In Radix sort, if the i-th digits are sorted, then the numbers consisting of i, i-1, ...,1 digits are sorted..

Proof. (Inductive proof)
Base step. Lemma holds for i = 1
Inductive step.
Induction Hypothesis. Assume for j < i, the lemma holds.
Prove it holds for i.