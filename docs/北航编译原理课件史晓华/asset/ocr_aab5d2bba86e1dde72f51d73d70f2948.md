# （4）删除冗余代码

冗余代码就是毫无实际意义的代码，又称死代码(dead code)或无用代码(useless code)。

例如： `x := x + 0;`　　`x := x * 1;`　　等

又例：　`FLAG := TRUE`

```
IF FLAG THEN…
    …
ELSE…
```

> FLAG永真

另外在程序中为了调试常有如下：

```
`if debug then …` 的语句。
```

但当debug为false时，then后面的语句便永远不会执行，
这就是可删去的冗余代码。

> （可用条件编译 #if DEBUG 编写程序，而源代码中还应留着）