+   举例：

请为下列表达式生成没有暂停的指令序列：

```
A = B + C ;
D = E − F ;
```

假设载入延迟为1个时钟周期。

题解

| 调度前的代码 | 调度后的代码 |
|---|---|
| LD    Rb, B | LD    Rb, B |
| LD    Rc, C | LD    Rc, C |
| DADD  Ra, Rb, Rc | LD    Re, E |
| SD    Ra, A | DADD  Ra, Rb, Rc |
| LD    Re, E | LD    Rf, F |
| LD    Rf, F | SD    Ra, A |
| DSUB  Rd, Re, Rf | DSUB  Rd, Re, Rf |
| SD    Rd, D | SD    Rd, D |