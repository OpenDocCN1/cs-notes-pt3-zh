# § 5.2 CSP理论

# CSP进程P的执行规则：

+   - ⟨skip, σ⟩ → σ
+   - ⟨abort, σ⟩ → abortion
+   - ⟨a, σ⟩ → n
+     ⟨x := a, σ⟩ → σ[n/x]
+   - ⟨P?x, σ⟩ \xrightarrow{P?n} σ[n/x]
+   - ⟨a, σ⟩ → n
+     ⟨P!a, σ⟩ \xrightarrow{P!n} σ