# # Extraneous Attributes (无关属性)

(形式化表示)

# ## Consider the functional dependency \(\alpha \rightarrow \beta\) in \(F\).

+   - Attribute A is **extraneous** in \(\alpha\), if \(A \in \alpha\) and \(F\) logically implies \(F' = (F - \{\alpha \rightarrow \beta\}) \cup \{(\alpha - A) \rightarrow \beta\}\).

+   - E.g. \(\alpha = \{A\alpha'\}, \{A\alpha'\} \rightarrow \beta\). 若 \(F\) 蕴涵 \(\alpha' \rightarrow \beta\), 则 \(\{A\alpha'\} \rightarrow \beta\) 多余，即 A 多余。

+   - Example: Given \(F = \{A \rightarrow C, AB \rightarrow C\}\)

+   - Because \(F = \{A \rightarrow C, AB \rightarrow C\}\) logically implies \(A \rightarrow C\), .: \(B\) is extraneous in \(AB \rightarrow C\),

+   - \(F' = \{A \rightarrow C, A \rightarrow C\} = \{A \rightarrow C\}\)

+   - Attribute A is **extraneous** in \(\beta\), if \(A \in \beta\) and the set of functional dependencies \(F' = (F - \{\alpha \rightarrow \beta\}) \cup \{\alpha \rightarrow (\beta - A)\}\) logically implies \(F\).

+   - E.g. \(\beta = A\beta'\), \(\alpha \rightarrow \{A\beta'\}\), 有 \(\{\alpha \rightarrow A, \alpha \rightarrow \beta'\}\). 若 \(F'\) 蕴涵 \(\alpha \rightarrow A\), 则 \(\alpha \rightarrow A\) 多余， (即可用 \(F'\) 代替 \(F\))。

+   - Example: Given \(F = \{A \rightarrow C, AB \rightarrow CD\}\)

+   - Since \(AB \rightarrow CD \Rightarrow \{AB \rightarrow C, AB \rightarrow D\}\). and \(AB \rightarrow C\) can be inferred from \(F' = \{A \rightarrow C, AB \rightarrow D\}\), .: \(C\) is extraneous in \(AB \rightarrow CD\)