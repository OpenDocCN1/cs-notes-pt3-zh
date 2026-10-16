# Efficient Implementation

# Women rejecting/accepting.

+   - Does woman w prefer man m₁ to man m₂?
+   - For each woman, create inverse of preference list of men.
+   - Constant time access for each query after O(n) preprocessing.

| Amy | 1st | 2nd | 3rd | 4th | 5th | 6th | 7th | 8th |
|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| Pref | 8 | 3 | 7 | 1 | 4 | 5 | 6 | 2 |

| Amy | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
|-----|---|---|---|---|---|---|---|---|
| Inverse | 4th | 8th | 2nd | 5th | 6th | 7th | 3rd | 1st |

```
for i = 1 to n
inverse[pref[i]] = i
```

Amy prefers man 3 to 6
since inverse[3] < inverse[6]
2      7