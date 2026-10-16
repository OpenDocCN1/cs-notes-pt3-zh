# The halting problem

We can easily prove that $A_{TM}$ is Turing-recognizable.

+   - $U=$“On input $<M, w>$, where $M$ is a TM and $w$ is a string:
+     1. Simulate $M$ on input $w$.
+     2. If $M$ accepts, *accept*; if it rejects, *reject*”