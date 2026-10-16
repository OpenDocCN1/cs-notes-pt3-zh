# 转换程序

综上所述，若要求对AD574进行12位A/D转换，连续采样100次，转换结果依次存入2000H:1000H开始的内存单元，可写出AD574在查询方式下的转换程序：

```
STA:    MOV     AX, 2000H
        MOV     DS, AX          ; 段地址
        MOV     DI, 1000H       ; 偏移地址
        MOV     CX, 100         ; 采样次数
X1:     OUT     80H, AL         ; 启动 12 位转换
        NOP                     ; 同步
X2:     IN      AL, 84H         ; 读状态 STS
        TEST    AL, 01H         ; STS=0（AD574 转换完成）？
        JNZ     X2              ; 不为 0，正在转换，继续查询
        IN      AL, 82H         ; 读高 8 位
        MOV     AH, AL
        IN      AL, 83H         ; 读低 4 位
        MOV     [DI], AX        ; 存 12 位数据
        ADD     DI, 2           ; 下一个字地址
        LOOP    X1
......
```