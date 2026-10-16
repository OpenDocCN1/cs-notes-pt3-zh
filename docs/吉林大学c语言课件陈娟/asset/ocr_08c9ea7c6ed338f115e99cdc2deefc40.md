# 上半部分

# Pattern Rows

| Row | Pattern |
|-----|---------|
| 1 | A B C D E F G |
| 2 | B C D E F G A |
| 3 | C D E F G A B |
| 4 | D E F G A B C |
| 5 | E F G A B C D |
| 6 | F G A B C D E |
| 7 | G A B C D E F |

```
for(j=i; i<=7; j++)
打印字符 'A'+j-
1
for(i=1; j<i; j++)
打印字符 'A'+j-
1
for(k=1; k<6-i; k++)
打印空格
for(k=1; k<2*i; k++)
打印字符 'A'+i-
1
for(k=1; k<6-i; k++)
打印空格
for(l=i+1; l<=7; l++)
打印字符 'A'+l-
1
for(l=1; l<=i; l++)
打印字符 'A'+l-
```