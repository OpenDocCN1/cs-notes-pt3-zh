# Proofs of functionally complete

+   - Transition to the system $\{\neg, \land\}$ or $\{\neg, \lor\}$:
+     - $A \land B \Leftrightarrow \neg(\neg A \lor \neg B)$,
+     - $A \lor B \Leftrightarrow \neg(\neg A \land \neg B)$

+   - The system $\{\neg, \land, \lor\}$ is sufficient according to the above statement.

+   - Transition to the system $\{\neg, \to\}$:
+     - $A \lor B \Leftrightarrow \neg A \to B$,
+     - $A \land B \Leftrightarrow \neg(A \to \neg B)$

+   - Transition to the system $\{\uparrow\}$ or $\{\downarrow\}$:
+     - $\neg A \Leftrightarrow A \uparrow A$, $A \land B \Leftrightarrow (A \uparrow B) \uparrow (A \uparrow B)$, ($\uparrow$ is NAND),
+     - $\neg A \Leftrightarrow A \downarrow A$, $A \lor B \Leftrightarrow (A \downarrow B) \downarrow (A \downarrow B)$, ($\downarrow$ is NOR).