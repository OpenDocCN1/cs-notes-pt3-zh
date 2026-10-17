# Skolemization

+   - Process for removing existential quantifiers.
+   - Delete each existential quantifier, then replace the resulting free variables by terms referred to as Skolem functions.
+   - ∃x∀y P(x,y) becomes ∀y P(c, y)
+   - ∀x∃y P(x,y) becomes ∀x P(x, f(x))
+   - Skolemization preserves satisfiability.