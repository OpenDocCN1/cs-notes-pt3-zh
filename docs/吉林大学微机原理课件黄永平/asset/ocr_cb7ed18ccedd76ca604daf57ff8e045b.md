【例4.16】计算5！的程序示例，RESULT是保存阶乘的存储单元。
程序如下：

```
STACK        SEGMENT STACK
             DB 200 DUP (0)
STACK        ENDS
DATA         SEGMENT
N            DW 5
RESULT       DW ?
DATA         ENDS
CODE         SEGMENT
             ASSUME CS: CODE, SS: STACK, DS: DATA
```