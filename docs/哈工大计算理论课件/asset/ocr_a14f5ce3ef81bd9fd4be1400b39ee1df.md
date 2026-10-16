# Reductions via computation histories

+   - First, construct a LBA $B$ to test whether $L(B)$ is empty.
+   - $B$ recognizes all accepting computation histories for $M$ on $w$.
+   - If $M$ accepts $w$, this language contains one string (the sequence of computation configuration) and so is nonempty.
+   - If $M$ does not accept $w$, this language is empty.