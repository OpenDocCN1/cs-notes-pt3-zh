# 4.5.2 Error Recovery in LL(1) Parsers

+   • Given a non-terminal A at the top of the stack and an input token that is not in First(A) (or Follow(A), if ε is in First(A)), there are three possible alternative:
+   
+   1. Pop A from the stack.
+   2. Successively pop tokens from the input until a token is seen for which we can restart the parse.
+   3. Push a new non-terminal onto the stack

![](bbox=[0.779, 0.665, 0.999, 0.999])

![](bbox=[0.002, 0.908, 0.093, 0.989])