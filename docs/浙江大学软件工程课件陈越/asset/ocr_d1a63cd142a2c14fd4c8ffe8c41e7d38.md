# 2.7 Type Conversions

char<short int<int<unsigned<long<unsigned long<float<double

type conversions take place in:

+   - expression with multi-kinds of data
+   - assignments
+   - argument passing ( function call)
+   - explicit type conversion ( forced);

(type_name) expression

```
unsigned long int next=1;
int rand(void)
{
    next = next * 1103515245 + 12345;
    return (unsigned int)(next/65536) % 32768;
}
void srand(unsigned int seed)
{
    next=seed;
}
```

![](bbox=[0.0, 0.0, 0.185, 1.0])