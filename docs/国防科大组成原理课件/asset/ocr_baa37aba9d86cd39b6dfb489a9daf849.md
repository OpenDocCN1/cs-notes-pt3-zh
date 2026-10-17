# 流程控制语句 – 示例2

+   - switch-case采用一串比较实现

```
int st(int a,int b,int c)
{
    switch(a){
        case 15:
            c=b&0x0f;
        case 10:
            return c+50;
        case 12:
        case 17:
            return b+50;
        case 14:
            return b;
        default:
            return a;
    }
}

st:
    li  t0, 15
    beq t0, a0, 1f
    li  t0, 10
    beq t0, a0, 2f
    li  t0, 12
    beq t0, a0, 3f
    li  t0, 17
    beq t0, a0, 3f
    li  t0, 14
    beq t0, a0, 4f
    nop
    jr  ra
    move v0, a0
1:  andi a2, a1, 0x0f
2:  jr  ra
    addi v0, a2, 50
3:  jr  ra
    addi v0, a1, 50
4:  jr ra
    move v0, a1
```