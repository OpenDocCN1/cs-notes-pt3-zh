
## 1.6.1 Operand Addressing Modes

### I/O Port Addressing

### I/O Port Direct Addressing

An 8-bit I/O port address(Address between 00 and 0FFH) must be addressed with an immediate operand.

- IN AL, 20H ; input a byte from port 20h to AL
- OUT 63H, AL ; output a byte from AL to port 63h

### I/O Port Indirect Addressing

A 16-bit I/O port address(Address above 0FFH) must be addressed with a value in the DX register.

- MOV DX,3F8H
- IN AL, DX ; input a byte from port 3f8h to AL

## 1.6.2 Programming Memory Addressing Modes

- Programming Memory Addressing modes used with the JMP and CALL instructions
- Consist of three distinct forms:
  - Direct Programming Memory Addressing
  - Relative Programming Memory Addressing
  - Indirect Programming Memory Addressing

### Relative Programming Memory Addressing Modes

- The term relative means “relative to IP”
- The JMP instruction is a one-byte instruction, with a one-byte or a two-byte displacement that add to the IP. Both types can jump anywhere within the current code segment
  - A one-byte displacement is used in short jump
  - A two-byte displacement is used in near jump or call
- Relative JMP and CALL instructions contain either an 8-bit or a16-bit signed displacement that allows a forward memory reference or a reverse memory reference.

- All assemblers automatically calculate the distance for the displacement and select the proper one- or two-byte form.
  - An 8-bit displacement has a jump range of between +127 and -128 bytes from the next instruction; a 16-bit displacement has a range of ± 32K bytes.

| offset | Machine code | program |
|---|---|---|
| 0000 | 0405 | ST: ADD AL,05H |
| 0002 | 90 | NOP |
| 0003 | EBFB | JMP SHORT ST |
| 0005 | 90 | NOP |

### Indirect Programming Memory Addressing Modes

- Far Indirect

Far indirect jump instruction can use any relative register; and any relative register with a displacement to be the address of next instruction.

If (DS)=2500H, (SI)=1300H, (26300H)=4500H, (26302H)=32F0H, the after execute:

```
JMP DWORD PTR [SI]: CS=32F0H, IP=4500H
```

## 1.6.3 Stack Memory Addressing Modes

- What is stack?
  - Stack holds data temporarily stores the return address used by procedures.
  - The stack memory is a LIFO(last-in, first-out) memory.

- Stack memory addressing Modes
  - It is contained in a segment and identified by the segment selector in the SS register.
  - The SP register always point to an area of memory located within the stack segment.
  - Items are placed on the stack using the PUSH instruction and removed from the stack using the POP instruction.

### PUSH operation

- Whenever a word of data is pushed onto the stack, the high-order 8 bit are placed in the location addressed by SP-1; The low-order 8 bit are placed in the location addressed by SP-2.

- The SP is then decremented by 2 so that the next word of data is stored in the next available stack memory location.

### POP operation

- Whenever a word of data is popped from the stack, the low-order 8 bit are removed from the location addressed by SP. The high-order 8 bit are removed from the location addressed by SP+1.

- The SP is then incremented by 2.

### Note

- The PUSH and POP store or retrieve words of data—never byte—in the 8086 through the 80286 microprocessor. 80386 and above allow words or doublewords.
- Data may be popped off the stack into any register or any segment register except CS.
- The SP register add to SS × 10H to form the stack memory address in the real mode.

```
Example:
PUSH  AX
POP   DS
```
