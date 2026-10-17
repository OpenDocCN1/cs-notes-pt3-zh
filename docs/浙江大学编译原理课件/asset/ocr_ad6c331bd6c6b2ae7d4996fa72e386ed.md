# 3.4.1 Ambiguity grammars

specify that an operation is nonassociative, in that a sequence of more than one operator in an expression is not allowed.

```
exp → factor op factor | factor
factor → ( exp ) | number
op → + | - | *
```

![](bbox=[0.356, 0.631, 0.999, 0.999])