# Conflicting Instructions

+   - Let $I_i$ and $I_j$ be two Instructions of transactions $T_i$ and $T_j$ respectively. Instructions $I_i$ and $I_j$ **conflict** if and only if there exists some item Q accessed by both $I_i$ and $I_j$, and at least one of these instructions wrote Q.
+     1. $I_i$ = read(Q), $I_j$ = read(Q). $I_i$ and $I_j$ don't conflict.
+     2. $I_i$ = read(Q), $I_j$ = write(Q). They conflict.
+     3. $I_i$ = write(Q), $I_j$ = read(Q). They conflict
+     4. $I_i$ = write(Q), $I_j$ = write(Q). They conflict

+   - Intuitively, a conflict between $I_i$ and $I_j$ forces a (logical) temporal order between them.
+     - If $I_i$ and $I_j$ are consecutive in a schedule and they do not conflict, their results would remain the same even if they had been interchanged in the schedule.