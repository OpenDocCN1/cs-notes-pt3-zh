# 4.2.2 The LL(1) Parsing Table and Algorithm

• A Parsing Algorithm Using the LL(1) Parsing Table:

```
push the start symbol onto the top the parsing stack;
while the top of the parsing stack ≠ $ and the next
    input token ≠ $ do
    if the top of the parsing stack is terminal a
        and the next input token = a
    then (* match *)
        pop the parsing stack;
        advance the input;
    else if the top of the parsing stack is non-terminal A
        and the next input token is terminal a
        and parsing table entry M[A,a] contains production
A→X1X2....Xn
```