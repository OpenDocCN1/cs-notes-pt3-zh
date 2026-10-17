# # 谓词逻辑中的推理

# ## 例3：

已知前提\((\exists x)(R(x) \land (\forall y)(D(y) \rightarrow L(x, y)))\),
\((\forall x)(R(x) \rightarrow (\forall y)(S(y) \rightarrow \neg L(x, y)))\)

# ### 证明：

试推出结论：\((\forall x)(D(x) \rightarrow \neg S(x))\)

+   (1) \((\exists x)(R(x) \land (\forall y)(D(y) \rightarrow L(x, y)))\) P
+   (2) \((R(a) \land (\forall y)(D(y) \rightarrow L(a, y)))\) ES,(1)
+   (3) \(R(a)\) T,(2)
+   (4) \((\forall y)(D(y) \rightarrow L(a, y))\) T,(2)
+   (5) \(D(u) \rightarrow L(a, u)\) US,(4)
+   (6) \((\forall x)(R(x) \rightarrow (\forall y)(S(y) \rightarrow \neg L(x, y)))\) P
+   (7) \(R(a) \rightarrow (\forall y)(S(y) \rightarrow \neg L(a, y))\) US,(6)
+   (8) \((\forall y)(S(y) \rightarrow \neg L(a, y))\) T,(3),(7)