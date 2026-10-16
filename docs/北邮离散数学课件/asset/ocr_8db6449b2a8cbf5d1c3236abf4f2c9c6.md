# Thinking about Quantifiers

+   When the domain of discourse is finite, we can think of quantification as looping through the elements of the domain.

+   To evaluate ∀x P(x) loop through all x in the domain.
+     - If at every step P(x) is true, then ∀x P(x) is true.
+     - If at a step P(x) is false, then ∀x P(x) is false and the loop terminates.

+   To evaluate ∃x P(x) loop through all x in the domain.
+     - If at some step, P(x) is true, then ∃x P(x) is true and the loop terminates.
+     - If the loop ends without finding an x for which P(x) is true, then ∃x P(x) is false.

+   Even if the domains are infinite, we can still think of the quantifiers this fashion, but the loops will not terminate in some cases.