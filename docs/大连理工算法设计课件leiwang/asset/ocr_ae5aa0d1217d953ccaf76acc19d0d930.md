# # Pseudocode for Floyd-Warshall

```
```
for k ← 1 to n
    do for i ← 1 to n
        do for j ← 1 to n
            do if cij > cik + ckj
                then cij ← cik + ckj
```
```

# ## Notes:

+   - Okay to omit superscripts, since extra relaxations can’t hurt.
+   - Runs in \(\Theta(n^3)\) time.
+   - Simple to code.
+   - Efficient in practice.