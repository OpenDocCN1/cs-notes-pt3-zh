# System Specification Example

+   - Predicate logic is used for specifying properties that systems must satisfy.
+   - For example, translate into predicate logic:
+     - “Every mail message larger than one megabyte will be compressed.”
+     - “If a user is active, at least one network link will be available.”
+   - Decide on predicates and domains (left implicit here) for the variables:
+     - Let L(m, y) be “Mail message m is larger than y megabytes.”
+     - Let C(m) denote “Mail message m will be compressed.”
+     - Let A(u) represent “User u is active.”
+     - Let S(n, x) represent “Network link n is state x.”
+   - Now we have: ∀m(L(m, 1) → C(m))
+     ∃u A(u) → ∃n S(n, available)