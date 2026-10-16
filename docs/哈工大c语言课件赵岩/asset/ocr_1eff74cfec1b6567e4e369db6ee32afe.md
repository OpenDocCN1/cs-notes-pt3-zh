# printf实例

# Demo 9: printf example

```
1 float  f1 = 100.15799, f2 = 12.55, f3 = 1.7;
2 int    n1 = 123, n2 = 45, n3 = 6;
3 printf("printf WITHOUT width or precision specifications:\n");
4 printf("%f\n%f\n%f\n", f1, f2, f3);
5 printf("%d\n%d\n%d\n", n1, n2, n3);
6
7 printf("printf WITH width and precision specifications:\n");
8 printf("%5.2f\n%6.1f\n%3.0f\n", f1, f2, f3);
9 printf("%5d\n%6d\n%3d\n\n", n1, n2, n3);
```