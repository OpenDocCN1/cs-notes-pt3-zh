# 5.7 ERROR RECOVERY IN BOTTOM-UP PARSERS

+   1. **Pop** states from the parsing stack until a state is found with nonempty Goto entries.
+   
+   2. If there is a legal action on the current input token from one of the Goto states, **push** that state onto the stack and restart the parse.
+   
+   3. If there is no legal action on the current input token from one of the Goto states, **advance** the input.

![](bbox=[0.777, 0.668, 1.0, 0.999])

![](bbox=[0.0, 0.915, 0.082, 0.999])