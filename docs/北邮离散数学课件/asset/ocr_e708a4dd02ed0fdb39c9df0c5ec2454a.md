# 关系的闭包/Closure of Relations

[定义1]: 称 R ∪ I_A 是 R 的自反闭包/reflexive closure of R, 记为 r(R)。

[定理1]: 设 R 是 A 上的二元关系, 则 r(R) 是包含 R, 具有自反性的最小关系。

证明: 对 ∀ x ∈ A, (x, x) ∈ I_A ⊆ R ∪ I_A, 且 R ⊆ R ∪ I_A。

若 R' 为包含 R 且具有自反性, 则 I_A ⊆ R', R ⊆ R', I_A ∪ R ⊆ R'。即 I_A ∪ R 为最小。

[推论1]: R 是自反闭包当且仅当 R 是自反的。

证明:

+   (1) R 是自反闭包, R = I_A ∪ R ⇒ I_A ⊆ R;
+   (2) R 具有自反性, I_A ⊆ R, R ∪ I_A = R;