```
ONE:    LOAD 2
        ADD =1
        STORE 2
NEXT: READ 1        （读入输入带上的下一个数）
        JMP REPEAT    （跳回REPEAT进行检查）
END: LOAD 2 (结束，将差值寄存器的值读入累加器)
    JZERO EQUAL （如果为零，说明1和2的个数相等，跳到EQUAL）
        WRITE =0        （将不相等的结果0写到输出带中）
        HALT    （程序结束，系统停机）
EQUAL:  WRITE =1    （相等，则输出1到输出带中）
        HALT        （程序结束，系统停机）
```