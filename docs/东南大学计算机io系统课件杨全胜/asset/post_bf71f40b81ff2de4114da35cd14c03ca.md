
## Chapter 2: IA-32 Assembly Language and Programming(1)

### Outline

- Assembly Language Programming
- Assembly Language Statements
- Directives
- Assembly Language Source Code
- User Interface Programming
- Instructions and Programming

### 2.1 Assembly Language Programming

#### Hello, Assembly Language!

```asm
.8086                  ; create 16 bit code
.model small           ; 32 bit memory model
.stack                 ; reserve stack
.data                  ; reserve storage for data
    MSG BYTE "Hello, Assembly Language!",13,10 ,'$'
.code                  ; Tell MASM where the code starts
start:  mov ax,@data
        mov ds,ax
        mov dx,offset msg  ; output MSG
        mov ah,09h
        int  21h
        mov ax,4c00h       ; return to OS
        int  21h
end start              ; Tell MASM where the program ends
```

How to ...

![](img/d7c975450dfbe59120092c2721be78c6_92_0.png)

#### Text Editors

- Source code files are text file
  - Text file is a collection of ASCII codes.
  - The extension name of assembly source file is .ASM
  - Example: hello.asm
- Text Editor is a Software to create or modify text files that are stored on the disk
  - Notepad2
  - Notepad
  - Edit

- Assembler
  - translates assembly language into machine code.
  - ml /c /Zd /Zi /Zm /Zf sample.asm
  - MASM sample.asm

- Linker
  - link object code to make a program that can be executed.
  - Link /CODEVIEW /NOD /DEB /DEBUGB /STACK:1024 sample.obj

#### Debugger

allows a programmer to control execution of a program, pausing after each instruction or at a preset breakpoint.

- Debug.exe
- SoftIce.exe
- Ollydbg.exe
- Windbg.exe
- Vkdebug.exe

### 2.2 Assembly Language Statements

- Three types of functional assembly language statements
  - Instructions
    - Can be translated into machine code (object code)
    
    ```asm
    [name:] mnemonic [[dest][,src]][:comment]
    [ ] = optional;
    dest and src are Operand
    ```
  - Directives
    - Tell the assembler to take some action, not result in machine code
    
    ```asm
    [name] directive [[operand][,operand,...]][:comment]
    [ ] = optional;
    ```
  - macros
    - Shorthand for a sequence of other statements

#### Name

- Identifier defined by the user, it may be a label or a variable.
- Available symbols can use in name is 'a'~'z', 'A'~'Z', '0'~'9', '?', '_', '@', '$'
- Length does not exceed 31 characters, first character can not be digit.

#### Comments

- Begin with the semicolon(;) and extends until the end of the line

### 2.3 Directives

#### Data Define

##### Data Types

| Type | Abbr | size | Integer range | Types Allowed |
|---|---|---|---|---|
| [S]BYTE | DB | 1 byte | -128~+255 | character, string |
| [S]WORD | DW | 2 byte | -32768~+65535 | 16-bit near ptr, 2 characters, double byte character |
| [S]DWORD | DD | 4 byte | -2Gig~+4Gig-1 | 16-bit far ptr, 32-bit near ptr, 32-bit long word |
| FWORD | DF | 6 byte | -- | 32-bit far pointer |
| QWORD | DQ | 8 byte | -- | 64-bit long word |
| TBYTE | DT | 10 byte | -- | BCD, 10-byte binary numbers |
| REAL4 | DD | 4 byte | -- | Single-precision floating point |
| REAL8 | DQ | 8 byte | -- | Double-precision floating point |
| REAL10 | DT | 10 byte | -- | 10-byte floating point |

##### Radix Specifiers

| Name | Base | Specifier | Digits |
|---|---|---|---|
| Binary | 2 | Y or B | 0 1 |
| Octal | 8 | Q or O | 0 1 2 3 4 5 6 7 |
| Decimal | 10 | T or D | 0 1 2 3 4 5 6 7 8 9 |
| Hexadecimal | 16 | H | 0 1 2 3 4 5 6 7 8 9 A B C D E F |
| Floating-point | 10 | R | 0 1 2 3 4 5 6 7 8 9 . E + - |

- Place the specifier at the end of the number.
- Hexadecimal numbers must always start with a decimal digit (0-9). If the first digit is one of the letters A to F, prefix the number with a leading 0 to distinguish it from a symbolic name.
