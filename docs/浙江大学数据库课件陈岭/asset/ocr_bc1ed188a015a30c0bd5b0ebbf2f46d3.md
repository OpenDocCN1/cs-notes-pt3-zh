# Example of Computing a Canonical Cover

+   - \(R = (A, B, C)\)
+   - \(F = \{ A \to BC,\ B \to C,\ A \to B,\ AB \to C \}\)

+   - Combine \(A \to BC\) and \(A \to B\) into \(A \to BC\)
+     - Set is now \(F' = \{A \to BC,\ B \to C,\ AB \to C\}\)

+   - \(A\) is extraneous in \(AB \to C\)
+     - Check if the result of deleting A from \(AB \to C\) is implied by the other dependencies \(B \to C\)
+     - Set is now \(F' = \{A \to BC,\ B \to C\}\)

+   - \(C\) is extraneous in \(A \to BC\)
+     - Check if \(A \to C\) is logically implied by \(A \to B\) and \(B \to C\)

The canonical cover is: \(F_c = \{A \to B,\ B \to C\}\)