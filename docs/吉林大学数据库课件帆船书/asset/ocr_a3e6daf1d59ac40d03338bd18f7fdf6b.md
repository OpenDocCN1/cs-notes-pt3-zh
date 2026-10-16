# Select Operation

+   - Notation: σₚ(r)
+   - p is called the selection predicate
+   - Defined as:

σₚ(r) = { t | t ∈ r and p(t) }

Where p is a formula in propositional calculus consisting of terms connected by : ∧ (and), ∨ (or), ¬ (not)

Each term is one of:

<attribute> op <attribute> or <constant>

where op is one of: =, ≠, >, ≥, <, ≤

+   - Example of selection:

σ dept_name="Physics"(instructor)