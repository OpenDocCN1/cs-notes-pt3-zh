# 2.6.7 Procedure Instructions

# Passing Parameters

# Passing Parameters in 16-bit program

# Example

**Input** 10 numbers in an array, then calculate the sum of is elements.

```
```asm
.8086
.MODEL SMALL
.DATA
    ARRAY  WORD 10 DUP(?)
    COUNT  WORD 10
    SUM    WORD ?
    STRING BYTE 6 DUP(?)
.STACK 1024
```
```