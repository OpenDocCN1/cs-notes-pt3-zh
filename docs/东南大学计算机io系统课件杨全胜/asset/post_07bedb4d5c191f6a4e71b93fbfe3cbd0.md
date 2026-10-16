
## 2.6.6 String Instructions

### String Comparisons Instruction

SCAS Example:

Search 'a' in the string "That is CAI", if found, then jump to FOUND

```
String BYTE "That is CAI"
......
CLD
LEA EDI, String
MOV AL, 'a'
MOV CX, 11
REPNZ SCASB
JZ FOUND
......
FOUND:
```

### String Comparisons Instruction

### CMPS Instruction

- Compare a byte, word, or double word from the data segment location addressed by (E)SI with the extra segment location addressed by (E)DI.
- can also with a REPZ/REPE or REPNZ/REPNE prefix.

| Assemble Language | Operation |
|---|---|
| CMPSB | DS:[SI]-ES:[DI]; if (DF=0) DI=DI+1 else DI=DI-1 |
| CMPSW | DS:[SI]-ES:[DI]; if (DF=0) DI=DI+2 else DI=DI-2 |
| CMPSD | DS:[SI]-ES:[DI]; if (DF=0) DI=DI+4 else DI=DI-4 |

### String Comparisons Instruction

> **CMPS Example**  
> Compare string1 and string2, if they are the same, then jump to NEXT

```
String1  DB 'HELP'
String2  DB 'HEPP'

.....
CLD
LEA  SI, String1
LEA  DI, String2
MOV  CX, 4
REPZ CMPSB
JZ   NEXT

.....
NEXT:
```

### String Comparisons Instruction

Example:

Compare SOURCE and DESTIN, if not same, load the first char in SOURCE that not match into AL register

```
...
LEA SI, SOURCE
LEA DI, DESTIN
CLD
MOV CX,100
REPZ CMPSB
JCXZ MATCH
DEC SI ; When terminal the loop, (E)SI and
; (E)DI point to the next position
LODSB
...
```

MATCH:

## 2.6.7 Procedure Instructions

- Basic of Procedure
- Procedure Instructions
- Procedure Define
- Passing Parameters

### Basic of Procedure

- A procedure is a group of instruction that usually perform one task.
- A procedure is a reusable section of the software that is stored in memory once, but use as often as necessary.
- Procedure can be called by other program.
- The CALL instruction link to the procedure and the RET instruction return from the procedure.
  - Link and return take the computer a small amount of time.
  - The stack stores the return address.

### Procedure Instructions

- **CALL**
  - Transfers the flow of the program to the procedure.
  - CALL differs from the JMP because a CALL pushes the return address onto the stack.
- **RET**
  - Pops the return address off the stack and returns control to that location (the instruction that follow the CALL in the program).

![](img/d7c975450dfbe59120092c2721be78c6_271_0.png)

### Procedure Instructions

Far call to different segment (.model small for 8086)

```
CALL FAR PTR procname
```

Direct call

- 1. SP<--(SP)-2
- 2. ((SP)+1,(SP))<--(CS)
- 3. SP<--(SP)-2
- 4. ((SP)+1,(SP))<--(IP)
- 5. IP<-- offset of procname
- 6. CS<-- seg of procname

### Procedure Instructions

Far call to different segment (.model small for 8086)

```
CALL DWORD PTR mem32/48
```

Indirect call

- 1. (E)SP<--((E)SP)-2
- 2. (((E)SP)+1,((E)SP))<--(CS)
- 3. SP<--(SP)-2/4
- 4. (((E)SP)+1/3,((E)SP))<--((E)IP)
- 5. (E)IP<--(EA)
- 6. CS<--(EA+2/4)

### Procedure Instructions

◆ call (.model flat for 80386 or above)

```
CALL  procname
```

☞ Direct call

- 1. ESP←(ESP)-4
- 2. ((ESP)+3,(ESP)+2,(ESP)+1,(ESP))←(EIP)
- 3. EIP←(EIP)+disp32

```
CALL  reg/mem32
```

☞ Indirect call

- 1. ESP←(ESP)-4
- 2. ((ESP)+3,(ESP)+2,(ESP)+1,(ESP))←(EIP)
- 3. EIP←reg32 or EIP←mem32

### Procedure Instructions

- Return from procedure

```
RET [exp]
```

| Assembly | function | operation |
|---|---|---|
| RET | return in current segment | IP<--((SP)+1,(SP)) SP<--(SP)+2 |
| RET | return from different segment | IP<--((SP)+1,(SP)) SP<--(SP)+2 CS<--((SP)+1,(SP)) SP<--(SP)+2 |
| RET EXP | return with data | besides above, do SP<--(SP)+EXP |
