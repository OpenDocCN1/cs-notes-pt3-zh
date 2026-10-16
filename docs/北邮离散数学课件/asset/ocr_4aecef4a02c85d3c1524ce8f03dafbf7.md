# Warshall’s Algorithm

```
Algorithm Warshall
CLOSURE←MAT
    For k = 1 thru N
        For i = 1 thru N
            For j = 1 thru N
                CLOSURE[i,j]←CLOSURE[i,j]
                    ∨(CLOSURE[i,k]∧CLOSURE[k,j])
End of Algorithm Warshall
```