# Advantage of Tail-recursion

+   - The activation record of a function is needed only as long as there is computation left over
+     - As soon as the return value is known – the activation record can be thrown away
+   - For tail-recursion
+     - No computation is needed after recursion
+     - Thus, original stack frame isn’t really needed
+     - The recursive callee can reuse caller’s stack frame – saving spaces