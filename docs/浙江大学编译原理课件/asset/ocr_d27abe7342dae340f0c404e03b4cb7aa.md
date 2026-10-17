# 7.3.1 Stack-Based Environments Without Local Procedures

# Local Temporaries and Nested Declarations

+   - **Nested declarations present a similar problem.**

```
Void p( int x, double y)
{
    char a;
    int i;
    ...
    A: {double x;
            int j;
            ...
        }
    ...
    B:{char *a;
            int k;
            ...
        }
    ...
}
```

![](bbox=[0.783, 0.663, 1.0, 0.999])

![](bbox=[0.0, 0.913, 0.099, 0.999])