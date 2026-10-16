# The Proof

+   - Given any *arbitrary* program *H(P, I)*,
+   - Consider algorithm *Breaker*, defined as:
+   
+     **procedure** *Breaker(P: a program)*
+   
+     &nbsp;&nbsp;&nbsp;&nbsp;*halts := H(P, P)*
+   
+     &nbsp;&nbsp;&nbsp;&nbsp;**if** *halts* **then while** T **begin end**

+   - Note that *Breaker(Breaker)* halts if
+     *H(Breaker, Breaker) = F*.

+   - So *H* does **not compute** the function
+     *Halts!*

> Breaker makes a liar out of H, by doing the opposite of whatever H predicts.