# 1.2.6 RCL和RCR指令

RCL（rotate carry left）指令按位左移，并将CF拷贝到最低有效位，然后将最□有效位拷贝至CF中；

![](bbox=[0.12, 0.35, 0.88, 0.55])

```
CLC
MOV $0x88, %BL
RCL $1, %BL
RCL $1, %BL
```

```
.data
testval: .byte 0x6a

shrb $1, testval
jc quit
rclb $1, testval
```