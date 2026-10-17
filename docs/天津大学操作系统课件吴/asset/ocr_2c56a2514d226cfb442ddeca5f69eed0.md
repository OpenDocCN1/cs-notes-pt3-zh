![](bbox=[0.017, 0.032, 0.256, 0.294])

S = 1 -> 0

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

Runnable

```
P (Semaphore s){
    while (!s>0)
        yield;
    s--;
}
```

```
V (Semaphore s){
    s++;
}
```