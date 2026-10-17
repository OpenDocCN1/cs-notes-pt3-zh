# Recursive Algorithm for MPC

```
int RC(int i, int j) {
    // Return c(i, j) and complete key(i, j) array[s]
    // Base cases
    // if i == j return 0
    // if c[i][j] > 0 return c[i][j]
    // if (i == j - 1) return 0;
    // if (i == j - 1) return 0;
    // ...
    return c[i][j];
}
```

```
void Traceback(int i, int j, int *key)
{
    if (i == j) return;
    Traceback(i, key[i][j], key);
    Traceback(key[i][j] + 1, j, key);
    cout << "(" << "M" << key[i][j] << ")";
}
```