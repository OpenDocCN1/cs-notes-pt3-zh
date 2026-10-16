# Negating nested quantifiers

+   - Example 12 There does not exit a woman who has taken a fliaht on everv airline in the world.
+     ∃w ∀a ∃f(P(w, f) ∧ Q(f, a))
+     ¬∃w∀a∃f(P(w, f) ∧ Q(f, a))
+     ⇔ ∀w¬∀a∃f(P(w, f) ∧ Q(f, a))
+     ⇔ ∀w∃a¬∃f(P(w, f) ∧ Q(f, a))
+     ⇔ ∀w∃a∀f¬(P(w, f) ∧ Q(f, a))
+     ⇔ ∀w∃a∀f(¬P(w, f) ∨ ¬Q(f, a))