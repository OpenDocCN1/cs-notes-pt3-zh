# Pseudo

```
RABIN-KARP-MATCHER(T, P, d, q)
n = T.length
m = P.length
h = d^(m-1) mod q
p = 0
t[0] = 0
for i = 1 to m
    p = (d*p + P[i]) mod q
    t[0] = (d*t[0]+T[i]) mod q
for s = 0 to n-m
    if p == t[s]
        if P[1..m] == T[s+1..s+m]
            print ("Find P with shift: "+s)
    if s < n-m
        t[s+1] = (d*(t[s]-T[s+1]*h) + T[s+m+1]) mod q
```

Space Complexity:
O(n-m)

Time Complexity:
O(m*(n-m))