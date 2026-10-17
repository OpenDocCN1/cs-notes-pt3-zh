# 5.3.1 The SLR(1) Parsing Algorithm

+   - A reduction by the rule S' → S, where S' is the start state, this will happen only if the next input token is $.
+   - Remove the string γ and all of its corresponding states from the parsing stack.
+   - Back up in the DFA to the state from which the construction of γ began.
+   - This state must contain an item of the form B → α·Aβ. Push A onto the stack, and push the state containing the item B → αA·β.

3. If the next input token is such that neither of the above two cases applies, an error is declared.

![](bbox=[0.778, 0.674, 0.999, 0.999])

![](bbox=[0.003, 0.915, 0.093, 0.988])