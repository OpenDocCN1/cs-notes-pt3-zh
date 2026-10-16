# Designing context-free grammars

+   - Example:
+     - The language {0^n1^n | n ≥ 0} ∪ {1^n0^n | n ≥ 0}
+     - For {0^n1^n | n ≥ 0}
+       S₁ → 0S₁1 | ε
+     - For {1^n0^n | n ≥ 0}
+       S₂ → 1S₂0 | ε
+     - So adding the new rule, we get
+       S → S₁ | S₂
+       S₁ → 0S₁1 | ε
+       S₂ → 1S₂0 | ε