# 2.3 Directives

# Data define

# Declaring and Referencing Arrays

LENGTHOF, SIZEOF, and TYPE for Arrays

```
array WORD 40 DUP (5)
larray EQU LENGTHOF array ; 40 elements
sarray EQU SIZEOF array      ; 80 bytes
tarray EQU TYPE array        ; 2 bytes per element
num DWORD 4, 5, 6, 7, 8, 9, 10, 11
lnum EQU LENGTHOF num        ; 8 elements
snum EQU SIZEOF num          ; 32 bytes
t num EQU TYPE num           ; 4 bytes per element
warray WORD 40 DUP (40 DUP (5))
len EQU LENGTHOF warray      ; 1600 elements
siz EQU SIZEOF warray        ; 3200 bytes
typ EQU TYPE warray          ; 2 bytes per element
```