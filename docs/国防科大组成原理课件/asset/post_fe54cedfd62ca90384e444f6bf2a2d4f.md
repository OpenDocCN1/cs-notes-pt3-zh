
## PowerPC特色—Link和Count寄存器

- **Link寄存器用于保存返回地址，实现快速过程调用**
- **Count寄存器用于循环计数，每次自动递减**
- 这两个寄存器还可以放转移地址
- **PowerPC不用Delay Slot**
- 其它特色
  - **Load和Store指令同时存取多个寄存器（多达32个）**
  - **Load和Store字符串（变长或定长、对齐或不对齐）**

## PA-RISC的Nullification

- 根据当前指令执行结果确定下一条指令是否执行

- 所有的转移指令和多数算术指令可用

- 如ADDB（Add and branch）指令在完成加法后，检查加法结果是否满足条件，如果不满足就转移。同时判断下一条指令（延迟槽）是否执行

- 可以消除一些简单的转移指令

```
if (a>b) s=a;
else  s=b;
```

| ADD | %r1, %r0, %r3 // r3 = r1(a) |
| SUB,*> | %r1, %r2, %r0 // r1(a) - r2(b) |
| ADD | %r2, %r0, %r3 // r3 = r2(b) |

- 其它指令系统有条件移数指令如 “CMOV”

- 后来演化为IA64的谓词技术

- 运算指令通过64个谓词寄存器决定结果是否保存

## Alpha和PowerPC指令功能举例

| 源代码: for (k=0; k<512; k++) x[k] = r * x[k] + t * y[k]; |
|---|
| PowerPC代码 | Alpha代码 |
| r3+8指向x<br>r4+8指向y<br>fp1内容为t<br>fp3内容为r<br>CTR内容为512<br>LOOP:<br>  LFU  fp0=y(r4=r4+8)  //FP load with update<br>  FMUL  fp0=fp0, fp1  //FP multiply<br>  LF   fp2=x(r3,8)    //FP load<br>  FMADD fp0=fp0, fp2, fp3 //FP multiply-add<br>  STFU x(r3=r3+8)=fp0 //FP load with update<br>  BC   LOOP, CTR>0   //decrement CTR, branch if>0 | r1指向x<br>r2指向y,<br>r6指向y的末尾<br>fp2内容为t<br>fp4内容为r<br>LOOP:<br>  LDT  fp3=y(r2,0)<br>  LDT  fp1=x(r1,0)<br>  MULT fp3=fp3, fp2 // t*y<br>  ADDQ r2=r2,8<br>  MULT fp1=fp1, fp4 // r*x<br>  SUBQ r4=r2, r6<br>  ADDT fp1=fp3, fp1 //t*y+r*x<br>  STT  x(r1,0)=fp1<br>  ADDQ r1=r1,8<br>  BNE  r4, LOOP |

## C语言的机器表示

## 流程控制语句

- • C语言的控制流语句
  - • 选择语句: if~else, switch~case
  - • 循环语句: for, while, do~while
  - • 辅助控制语句: break, continue, goto, return

- • C语言的控制流语句在MIPS汇编中映射为各种分支指令 (B类) 或其组合
  - • 选择语句和循环语句映射为条件分支
  - • 辅助控制语句映射为无条件分支或JR (return语句)

## 流程控制语句 – 示例1

- - 当条件表达式t0等于0（BEQZ）时，跳转到标号1
- - 标号2为公用的程序出口
- - 本例的延迟槽使用空指令（NOP）进行填充

| // C if ~ else | ## ASM if ~ else |
|---|---|
| if (cond_exp) | move t0, cond_exp |
| <then_statement> | beqz t0, 1f   # label1 forward |
| else | nop           # delay slot |
| <else_statement> | <then_statement> |
| | b 2f          # label2 forward |
| | nop           # delay slot |
| | 1: |
| | <else_statement> |
| | 2: |

## 流程控制语句 – 示例2

- - switch-case采用一串比较实现

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

## 流程控制语句 – 示例3

- • switch-case采用跳转表实现

```c
int st(int a,int b,int c)
{
  switch(a){
  case 15:
    c=b&0xf;
    return c+50;
  case 10:
    return b+50;
  case 12:
    return b;
  case 17:
    return b+50;
  case 14:
    return b;
  default:
    return a;
  }
}
```

```mips
st:
addi v0, a0, -10
sltiu v1, v0, 8
beqz v1, default
li v1, jr_table
sll v0, v0, 0x2
addi v1, v1, v0
lw v0, 0(v1)
jr v0
nop
default:
andi a2, a1, 0xf
case_10:
jr ra
addi v0, a2, 50
case_12017:
jr ra
addi v0, a1, 50
case_14:
jr ra
addi v0, a1, 0
default:
jr ra
addi v0, a0, 0
jr_table:
00: case_10
04: default
08: case_12017
0c: default
10: case_14
14: default
1c: case_12017
```

## 流程控制语句 – 示例4

| // C for<br>for(i=0; i<8; i++)<br>  sum += i; | ## ASM for<br>    move t0, $0<br>    li   t1, 8<br>1: add  t2, t0, t2<br>    addi t0, t0, 1<br>    bne  t0, t1, 1b # label1 backward<br>    nop |
| // C while<br>i = 0;<br>while (i < 8)<br>  i++; | ## ASM while<br>    move t0, $0<br>    li   t1, 8<br>1: bge  t0, t1, 2f<br>    nop<br>    b    1b<br>    addi t0, t0, 1  # delay slot<br>2: |
| // C do ~ while<br>i = 0;<br>do {<br>  i++;<br>}while (i < 8) | ## ASM do ~ while<br>    move t0, $0<br>    li   t1, 8<br>1: blt  t0, t1, 1b<br>    addi t0, t0, 1  # delay slot |
