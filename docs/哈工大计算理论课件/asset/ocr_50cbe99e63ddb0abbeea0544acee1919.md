# Co-Turing-recognizable language

+   - $M$=“On input string $w$:
+     1. Run $M_1$ on the first tape, and run $M_2$ on the second tape. (run in parallel)
+     2. If $M_1$ accepts, **accept**; if $M_2$ accepts, **reject**.”

+   - As the string of $A$ will be accepted by $M_1$. And the string not in $A$ will be accepted by $M_2$. So $M$ always halts and is a decider of $A$.