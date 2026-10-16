# 例7.8 对a<b and c<d and e<f的翻译

```
100:    if a<b goto 103    107:  t2 := 1
101:    t1:= 0            108: t3=t1 and t2
102:    goto 104          109: if e<f goto 112
103:    t1 := 1           110: t4=0
104:    if c<d  goto 107  111: goto 113
105:    t2 := 0           112: t4=1
106:    goto  108          113: t5=t3 and t4
```