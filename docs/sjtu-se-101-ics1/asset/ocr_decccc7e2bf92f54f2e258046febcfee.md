# Do-while Translation

```
do
    body-statement
while (test-expr)
```

```
loop:
    body-statement
    t = test-expr;
    if ( t )
        goto loop ;
```