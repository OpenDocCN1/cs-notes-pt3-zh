# # Generating Pointer to Structure Member

```
struct rec {
    int a[4];
    size_t i;
    struct rec *next;
};
```

![](bbox=[0.469, 0.167, 0.875, 0.375])

# ## Generating Pointer to Array Element

+   - Offset of each structure member determined at compile time
+   - Compute as r + 4*idx

```
int *get_ap
(struct rec *r, size_t idx)
{
    return &r->a[idx];
}
```

```
# r in %rdi, idx in %rsi
leaq (%rdi,%rsi,4), %rax
ret
```