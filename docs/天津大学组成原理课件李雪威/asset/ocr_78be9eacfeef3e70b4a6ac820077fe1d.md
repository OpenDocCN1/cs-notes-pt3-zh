# # Using Conditional Moves

# ## Conditional Move Instructions

+   - Instruction supports:
+     - if (Test) Dest ← Src

+   - Supported in post-1995 x86 processors

+   - GCC tries to use them
+     - But, only when known to be safe

# ## Why?

+   - Branches are very disruptive to instruction flow through pipelines

+   - Conditional moves do not require control transfer

# ## C Code

```
```c
val = Test
  ? Then_Expr
  : Else_Expr;
```
```

# ## Goto Version

```
```c
result = Then_Expr;
eval = Else_Expr;
nt = !Test;
if (nt) result = eval;
return result;
```
```