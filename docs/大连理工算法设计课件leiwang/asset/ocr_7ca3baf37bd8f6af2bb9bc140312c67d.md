# # Successor and predecessor

The successor of a node x is the node y such that key[y] is the smallest key > key[x]. (We can find x’s successor based entirely on the tree structure. No key comparisons are necessary.) If x has the largest key, then x’s successor is NIL.

```
TREE-SUCCESSOR(x)
1 if right[x] ≠ NIL
2 then return TREE-MINIMUM(right[x])
3 y ← p[x]
4 while y ≠ NIL and x = right[y]
5 do x ← y
6 y ← p[y]
7 return y
```

_Time:_ Since we visit nodes on a path down the tree or up the tree, the running time is _O_(_h_), where _h_ is the height of the tree.