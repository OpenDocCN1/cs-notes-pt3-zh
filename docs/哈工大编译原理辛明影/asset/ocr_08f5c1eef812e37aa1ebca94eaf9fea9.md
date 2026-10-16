例：布尔表达式 a<b  and  c<d and e<f 可以生成如下的三地址码

```
100:if a<b goto 103
101:t1=0
102:goto 104
103:t1=1
104:if c<d goto 107
105:t2=0
106:goto 108
107:t2=1
108:t3=t1 and t2
109:if e<f goto 112
110:t4=0
111:goto 113
112:t4=1
113:t5=t3 and t4
```