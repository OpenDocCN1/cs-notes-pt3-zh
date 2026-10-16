# 例2: (建立符号表表项时检查有无重复定义)

```
1. int x=10;
2. fun1()
3. {
4. int x=20, z;
5. int x=30;
6. ....
7. z=x+10;
8. ....
9. }
10. fun2()
11. {int x=30;
12. y=x+100;
13. }
```

| x | intPtr | varKind | dir | 0 | m | 10 |
| fun1 |  | routKind | ... | .... |  |  |
| fun2 |  | routKind | ... | .. | .... | .... |

| x | intPtr | varKind | dir | 1 | m | 20 |
| z | intPtr | varKind | dir | 1 | m+1 |  |

| x | intPtr | varKind | dir | 1 | m | 30 |