

## 6.5 应用

例如。某应用使用 82C55 采集开关 S7~S0 的状态，然后通过一组发光二极管(LED7~LED0) 显示开关的状态（当 Si 闭合时，IEDi 亮起）。查看下图，假设 8255 中的两个组都工作在模式 0。

- 1) 82C55 的端口地址是什么？
- 2) 控制字是什么？
- 3) 对 82C55 编程

- 1) 该 82C55 的端口地址是：
320H、321H、322H和323H。

- 2) Port A – mode 0, output, Port B – mode 0, input, so Control Word is 10000010b=82H

- 3) MOV AL, 82H ;write control word
MOV DX, 323H ;
OUT DX, AL
L1: MOV DX, 321H ;
IN AL, DX ;input switches state
NOT AL ;
MOV DX, 320H ;
OUT DX, AL ;output
JMP L1

**思考：**

如果将上一题的要求修改为：不使用查询，而是每 50ms 产生一次中断，在中断处理程序中读取端口 B 并写入端口 A。

如何修改电路和程序？

假设系统提供 2KHz 脉冲，8254 和 8259 地址与 PC 相同。

例如。现在将打印机与 82C55 的端口 A 模式 0 连接。编程打印 BUFF 中的字符

当 STB# 有效时，打印机接收数据，当 BUSY 有效时，表示打印机现在忙，不能接收数据。

## Computer I/O System

![](img/d7c975450dfbe59120092c2721be78c6_472_0.png)

![](img/d7c975450dfbe59120092c2721be78c6_473_0.png)

```asm
.DATA
BUFF    BYTE 'HELLO,WORLD!', 13, 10, '$'
PORTA   EQU 60H
PORTB   EQU 61H
PORTC   EQU 62H
PORTCN  EQU 63H

.CODE
START:  MOV     AX, @DATA
        MOV     DS, AX
        MOV     SI, OFFSET BUFF
```

; initial 8255, Port A mode 0, output, Port C upper is input, lower is output

```
MOV AL, 88H
OUT PORTCN, AL
MOV AL, 01H      ; set PC0, STB invalid
OUT PORTCN, AL
WAIT: IN AL, PORTC ; read status of printer
TEST AL, 80H      ; if "busy", wait
JNZ WAIT
MOV AL, [SI]
CMP AL, '$'
JZ PRINT_OVER
```

```
OUT PORTA, AL ; sent the data
MOV AL, 00H
; generate the STB#
OUT PORTCN, AL
MOV AL, 01H
OUT PORTCN, AL
INC SI
JMP WAIT
```

```
PRINT_OVER: MOV AH,4CH
             INT 21H

END START
```

## Computer Input/output System

2015

Instructors: Yang Quansheng

School of Computer Science and Engineering
College of Software Engineering
Southeast University

## Chapter 6:

## 16550 Programmable
Communications Interface

## Outline

- Serial Communication
- Asynchronous Serial Communication
- RS-232 Standard
- 16550 UART
- COM in IA-32

## 7.1 Serial Communication

## ■ Serial Communication

- 串行通信是通过通信信道或计算机总线一次发送一个比特、顺序发送数据的过程。
- 需要串行器和反串行器，或 SerDes
- 串行通信用于所有长距离通信和大多数计算机网络，在这些场景中，电缆成本和同步困难使得并行通信不切实际。

## Serial Communication

串行计算机总线即使在较短距离下也变得越来越常见，因为较新的串行技术中改进的信号完整性和传输速度开始超过并行总线在简单性方面的优势（无需串行器和反串行器，或 SerDes），并超过了其缺点（时钟偏移、互连密度）。

## Serial versus parallel

为了实现更高的数据速率，串行链路可以比并行链路时钟速度快得多，因为：

- 不同通道之间的时钟偏移不是问题。
- 串行连接需要更少的互连电缆，因此占用空间更少。额外的空间允许通道与其周围环境更好地隔离。
- 串扰问题较少，因为相邻的导体更少。

串行实现成本更低。

