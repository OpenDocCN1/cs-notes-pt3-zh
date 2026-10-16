```
{  j=1; FIRST(X)={}; //initiate
  while ( j<k and ε∈ FIRST(Yj)) {
    FIRST(X)=FIRST(X)∪(FIRST(Yj)-{ε})
    j=j+1
  }
  IF (j=k and ε∈ FIRST(Yk))
    FIRST(X)=FIRST(X) ∪ {ε}
}
```