# Decision-Tree Construction Algorithm

```
Procedure GrowTree (S)
    Partition (S);
```

```
Procedure Partition (S)
    if ( purity(S) > δₚ or |S| < δₛ ) then
        return;
    for each attribute A
        evaluate splits on attribute A;
    Use best split found (across all attributes) to partition
        S into S₁, S₂, ...., Sᵣ
    for i = 1, 2, ....., r
        Partition (Sᵢ);
```