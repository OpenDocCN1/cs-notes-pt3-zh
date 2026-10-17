# 6.1 局部存储分配策略

```
```c
main()
{
    /* begin of B₀ */
    int a = 0;
    int b = 0;
    /* begin of B₁ */
        int b = 1;
        /* begin of B₂ */
            int a = 2;
        }/* end of B₂ */
        /* begin of B₃ */
            int b = 3;
        }/* end of B₃ */
    }/* end of B₁ */
}/* end of B₀ */
```
```

| 声明 | 作用域 |
|---|---|
| `int a = 0;` | `B₀-B₂` |
| `int b = 0;` | `B₀-B₁` |
| `int b = 1;` | `B₁-B₃` |
| `int a = 2;` | `B₂` |
| `int b = 3;` | `B₃` |