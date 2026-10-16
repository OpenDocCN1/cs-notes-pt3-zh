# Space Hierarchy Theorem

+   - Proof Idea:
+     - Roughly, D takes its input to be the description of a TM M
+       - Reject if input is not a description of any TM
+     - $D$ runs $M$ on the same input, $<M>$ within the space bound $f(n)$
+     - If $M$ halts within that much space, $D$ accepts iff $M$ rejects
+     - If M does not halt, reject
+     - If M runs within the space bound $f(n)$, $D$ has enough space to ensure that its language is different from $M$'s
+     - It is okay that if $D$ does not have enough space to figure out what $M$ does, because $D$ is not required to act differently if $M$ does not run in $o(f(n))$ space