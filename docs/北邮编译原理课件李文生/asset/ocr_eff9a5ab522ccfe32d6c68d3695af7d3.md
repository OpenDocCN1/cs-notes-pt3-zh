# 分别与E→TM、M→+TM|ε 相应的分析过程

//E→TM

```
void proc_E(void) {
    proc_T();
    proc_M();
};
```

//M→+TM|ε

```
void proc_M(void) {
    if (lookahead== '+')
    {
        match('+');
        proc_T();
        proc_M();
    }
};
```