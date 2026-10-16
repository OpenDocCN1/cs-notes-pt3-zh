# Self-reference

+   - **Circular definition**: to define an object in terms of itself.
+   - We can’t define *B* (use a computational function *q(<A>)* )as we have done to *A* to avoid the circular definition.
+   - Define *B* as: *B* computes *A* from the output that *A* produces.
+   - As <*B*> is on the tape of machine *A* when *A* halts. And we can define *q(<B>)* = <*A*> to get the description of *A*.