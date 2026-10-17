# 6.2.2 Synthesized and inherited attributes

# Synthesized attributes

+   - The attribute values of an S-attributed grammar can be computed by a single bottom-up, or post-order, traversal of the parse or syntax tree.

```
Procedure PostEval (T : treenode);
Begin
    For each child C of T do
        PostEval(C);
        Compute all synthesized attributes of T;
End
```

![](bbox=[0.782, 0.668, 1.0, 0.999])

![](bbox=[0.0, 0.912, 0.086, 0.999])