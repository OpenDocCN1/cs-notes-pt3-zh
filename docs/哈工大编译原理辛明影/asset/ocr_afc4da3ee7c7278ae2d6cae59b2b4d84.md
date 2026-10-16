# 例5.16

```
R→addop

T { R1.i:=mknode(addop.lexeme,
R.i, T.nptr) }

R1 { R.s:=R1.s }

R→ε { R.s:=R.i }

(5.5)
```

# 递归下降构造语法树

```
function R(in: ↑ syntax-tree-node):
↑ syntax-tree-node;
var npt r,i1,s1,s: ↑syntax-tree-node;
addoplexeme:char;
```