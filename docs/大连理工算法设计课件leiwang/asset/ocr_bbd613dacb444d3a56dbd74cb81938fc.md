```
TREE-INSERT(T, z)
1  y ← NIL
2  x ← root[T]
3  while x ≠ NIL
4      do y ← x
5         if key[z] < key[x]
6             then x ← left[x]
7             else x ← right[x]
8  p[z] ← y
9  if y = NIL
10     then root[T] ← z
11     else if key[z] < key[y]
12             then left[y] ← z
13             else right[y] ← z
```

> ▷ Tree T was empty