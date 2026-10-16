# 2.6.6 String Instructions

# String Comparisons Instruction

SCAS Example:

Search 'a' in the string "That is CAI", if fount, then jump to FOUND

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