![](bbox=[0.017, 0.033, 0.258, 0.303])

S = 1 -> 0 -> -1 -> -2 -> -1

# C

```
P (Semaphore s){
    s=s-1;
    if (s<0){
        sleep…;
    }
}
```

```
V (Semaphore s){
    s=s+1;
    if (s<=0){
        wakeup…;
    }
}
```

```
Process A:
... ...
P(S);
Print(a.doc);
V(S);
... ...
```

Runnable

```
Process B:
... ...
P(S);
Print(b.doc);
V(S);
... ...
```

Runnable

```
Process C:
... ...
P(S);
Print(c.doc);
V(S);
... ...
```

Blocked