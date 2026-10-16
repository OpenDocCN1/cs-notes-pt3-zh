# 11.3.3 代码生成算法

前三条指令可以修改，使执行代价降低

```
MOV a, R0
SUB b, R0
MOV a, R1
SUB c, R1
... 
```

```
MOV a, R0
MOV R0, R1
SUB b, R0
SUB c, R1
... 
```