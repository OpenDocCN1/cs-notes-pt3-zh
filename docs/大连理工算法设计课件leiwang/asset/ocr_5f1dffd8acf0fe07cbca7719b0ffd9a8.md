# # TREE-SEARCH

```
TREE-SEARCH(x, k)
1 if x = NIL or k = key[x]
2 then return x
3 if k < key[x]
4 then return TREE-SEARCH(left[x], k)
5 else return TREE-SEARCH(right[x], k)
```

**_Time:_** The algorithm recurses, visiting nodes on a downward path from the root. Thus, running time is _O_(_h_), where _h_ is the height of the tree.