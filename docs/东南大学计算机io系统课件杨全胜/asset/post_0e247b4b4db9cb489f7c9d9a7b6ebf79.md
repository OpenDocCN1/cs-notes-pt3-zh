
## 2.5 User Interface Programming

| 指令 | 操作码 | 操作 |
|---|---|---|
| interrupt | **INT N** | SP←(SP)-2<br>((SP)+1,(SP))←(FLAGS)<br>SP←(SP)-2<br>((SP)+1,(SP))←(CS)<br>SP←(SP)-2<br>((SP)+1,(SP))←(IP)<br>IP←(0000:OA)　; OA=4*N<br>CS←(0000:OA+2) |
| Return | **IRET** | IP←((SP)+1,(SP))<br>SP←(SP)+2<br>CS←((SP)+1,(SP))<br>SP←(SP)+2<br>FLAGS←((SP)+1,(SP))<br>SP←(SP)+2 |

## 2.5 User Interface Programming

| n | function | n | function |
|---|---|---|---|
| 10H | Video Services | 13H | Low Level Disk Services |
| 14H | Serial port services | 15H | Miscellaneous system services |
| 16H | Keyboard services | 17H | Printer services |
| 20H | Terminate program | 21H | Main DOS API |
| 22H | Program terminate to calling program | 23H | Control-C handler address |
| 24H | Critical error handler address | 33H | Mouse services |

n - Interrupt vector number

INT n ; for example: INT 10H, INT 21H

## 2.5 User Interface Programming

### How to use the INT instructions

- Put function number in AH register
- Set all entrances parameters in accordance with the requirements
- Use INT n instructions

For example:

Set the screen in 640×480 16 color graphic mode

```
MOV AH, 0      ; function number
MOV AL, 12H     ; entrances parameters
INT  10H        ; video services
```

## 2.5 User Interface Programming

### Example

Print character ‘S’ to printer

```
MOV  AH, 1    ; initial the printer
MOV  DX, 0    ; Printer number
INT  17H      ;
MOV  AH, 0    ; print a character
MOV  DX, 0    ; printer number
MOV  AL, 'S'  ; character that will be print
INT  17H      ; print ‘S’
```

## 2.5 User Interface Programming

- Input a character from keyboard

- wait for a keystroke and return its code in AL

- Use DOS API

```
MOV  AH,1
INT  21H  ; ASCII code in AL
```

- Use BIOS API

```
MOV AH,0
INT  16H  ; ASCII code in AL, scan code in AH
```

- Return character from keyboard without waiting

```
MOV AH,1
INT  16H  ; if ZF=0, ASCII code in AL, scan
; code in AH
; if ZF=1, no key be stroked
```

## 2.5 User Interface Programming

- Output a character to screen

- Print a character in DL to screen

```
MOV DL, 'A'     ; char want to print
MOV AH, 02H
INT  21H
```

- How to input a character and output it?

```
MOV AH, 01H
INT  21H
MOV DL, AL
MOV AH, 02H
INT  21H
```

## 2.5 User Interface Programming

### Output a string to screen

```
```asm
.DATA
    MSG BYTE "Hello world!",0Ah,0Dh,'$'
.CODE
START:
    MOV AX, DATA
    MOV DS, AX
    MOV DX, OFFSET MSG
    MOV AH, 09H
    INT 21H
    MOV AH, 4CH
    INT 21H
END START
```
```

> **Tips:**  
> In order to output a carriage return and line feed (`\r\n` in C), you can define a string as follows:  
> `CR DB 0AH,0DH,'$'`

## 2.5 User Interface Programming

### Input a string from keyboard

```
N        EQU 20
MAXLEN   DB  N          ; max length of buff
ACTLEN   DB  ?          ; the actual length
STRING   DB  N DUP(?)   ; buff to store the string
.....
MOV      AH, 0AH
MOV      DX, OFFSET MAXLEN
INT      21H
```

# Computer Input/output System

2015

Instructors: Yang Quansheng

School of Computer Science and Engineering
College of Software Engineering
Southeast University

# Chapter 2:

# IA-32 Assembly Language and Programming(2)

## 2.6 Instruction and Programming

- General purpose instructions
- X87 FPU instructions
- MMX instructions
- SSE/SSE2/SSE3 instructions
- System instructions
- 64-bit mode instructions
- Virtual-machine extensions

## 2.6 Instruction and Programming

### General purpose instructions

- Data Movement Instructions
- Arithmetic Instructions
- Logic Instructions
- Jump instructions
- Loop instructions
- String Instructions
- Procedure Instructions

## 2.6.1 Data Movement Instructions

- MOV Instruction
- PUSH/POP Instruction
- Load-Effective Address Instruction
- Miscellaneous Data Transfers Instructions
