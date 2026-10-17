# 5.3 SLR(1) Parsing

•Definition:

The SLR(1) parsing algorithm.

+   1. If state s contains any item of form A → α·Xβ, then the action is to shift the current input token onto the stack, and the new state to be pushed on the stack is the state containing the item A → αX·β.

+   2. If state s contains the complete item A → γ·, and the next token in the input string is in Follow(A), then the action is to reduce by the rule A → γ.

![](bbox=[0.77, 0.676, 1.0, 0.999])

![](bbox=[0.0, 0.91, 0.082, 0.999])