# Solution

```
// recursive algorithm
PRINT-STATIONS(l, j, n) // initially j = n
    if ( j == n )
        i ← l*
    else
        i ← l_i[j+1]

    if ( j == 0 )
        return
    else
        if ( j > 1 )
            PRINT-STATION(l, j-1, n)
    print "line" i ", station" j
```

```
// non-recursive algorithm
PRINT-STATIONS(l, j, n)
    i ← l*
    A[n] ← i
    for j ← n downto 2
        i ← l_i[j]
        A[j-1] ← i
    for j ← 1 upto n
        print "line" A[j] ", station" j
```