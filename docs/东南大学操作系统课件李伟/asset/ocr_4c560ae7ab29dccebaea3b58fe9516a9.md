# Algorithm 3——Peterson’s Solution

+   - Combined shared variables of algorithms 1, 2.

+   - Process Pᵢ

```
do {
    flag[i] = true;
    turn = j;
    while (flag[j] and turn == j);
        critical section
    flag[i] = false;
        remainder section
} while (1);
```

+   - Meets all three requirements; solves the critical-section problem **for two processes**.