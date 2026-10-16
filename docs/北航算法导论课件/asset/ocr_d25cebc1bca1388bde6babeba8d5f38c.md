# 17.2 The accounting method - Stack operations

+   - The actual cost of the ith operation: $c_i$
+   - The amortized cost of the ith operation: $\hat{c}_i$ $\sum_{i=1}^{n} \hat{c}_i \ge \sum_{i=1}^{n} c_i$
+   - The actual costs of the operations
+     PUSH 1,
+     POP 1,
+     MULTIPOP min(k, s),
+   - We assign the following amortized costs
+     PUSH 2,
+     POP 0,
+     MULTIPOP 0.
+   - We can pay for any sequence of stack operations by charging the amortized costs?
+   - For any sequence of $n$ PUSH, POP, and MULTIPOP operations, the total amortized cost is O(n), so is the total actual cost.

```
STACK(S, n)
    S = NULL
    for i←1 to n
        One of ( PUSH(S, i), POP(S), MULIPOP(S, k) )
```