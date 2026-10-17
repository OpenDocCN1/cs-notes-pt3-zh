# # 六、集合之间的关系

# ## 3.集合的真包含

定义：如果集合\(A\)的每一个元素都属于\(B\)，但集合\(B\)中至少有一个元素不属于\(A\)，则\(A\)称为\(B\)的真子集，或\(A\)真包含于\(B\)，记作 \(A \subset B\)。

\(A \subset B \Leftrightarrow (\forall x)(x \in A \rightarrow x \in B) \wedge (\exists y)(y \in B \wedge y \notin A)\)
\(A \subset B \Leftrightarrow A \subseteq B \wedge A \neq B\)

例如：设\(A=\{0, 1\}\)，\(B=\{0, 1, 2\}\)，\(C=\{0\}\)
则\(A \subset B\)，\(C \subset A\)，\(\varnothing \subset C\)