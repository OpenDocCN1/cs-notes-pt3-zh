

![](img/9bd5f6161cb6607b56d2fb964d1b8794_255_0.png)

管道控制逻辑

| W | icode |  | valE | valM |  | dstE | dstM |
|---|---|---|---|---|---|---|---|

| M | icode | Bch |  | valE | valA |  | dstE | dstM |
|---|---|---|---|---|---|---|---|---|

E_icode

E_bubble

| E | icode | ifun | valC | valA | valP | dstE | dstM | srcA | srcB |
|---|---|---|---|---|---|---|---|---|---|

D_bubble

| D | icode | ifun | rA | rB | valC | valP |
|---|---|---|---|---|---|---|

| F | predPC |
|---|---|

srcA

srcB

## Return Example

```
#demo-retB.ys
0x000:     irmovl Stack,%esp   # Intialize stack pointer
0x006:     call p             # Procedure call
0x00b:     irmovl $5,%esi     # Return point
0x011:     halt
0x020: .pos 0x20
0x020: p: irmovl $-1,%edi     # procedure
0x026:     ret
0x027:     irmovl $1,%eax     # Should not be executed
0x02d:     irmovl $2,%ecx     # Should not be executed
0x033:     irmovl $3,%edx     # Should not be executed
0x039:     irmovl $4,%ebx     # Should not be executed
0x100: .pos 0x100
0x100: Stack:                 # Stack: Stack pointer
```

- Previously executed three additional instructions

## Correct Return Example

```
#demo_retb
1: 0x026: ret
2: bubble
3: bubble
4: bubble
5: 0x00b: irmovl $5, %esi #return
```

- As ret passes through pipeline, stall at F stage
  - While in D, E, and M stage
  - fetch the same instruction after ret 3 times.
- Inject bubble into D stage
- Release stall when reach W stage

![](img/9bd5f6161cb6607b56d2fb964d1b8794_257_0.png)

## Detecting Return

![](img/9bd5f6161cb6607b56d2fb964d1b8794_258_0.png)

执行

解码

## Control for Return

| Condition | Trigger |
|---|---|
| Processing ret | IRET in { D_icode, E_icode, M_icode } |

```
#demo_retb
1: 0x026: ret
2: bubble
3: bubble
4: bubble
5: 0x00b: irmovl $5, %esi #return
```

![](img/9bd5f6161cb6607b56d2fb964d1b8794_259_0.png)

| Condition | F | D | E | M | W |
|---|---|---|---|---|---|
| Processing ret | stall | bubble | normal | normal | normal |

![](img/9bd5f6161cb6607b56d2fb964d1b8794_260_0.png)

# Pipe control logic

M_icode

E_icode

D_icode

D_bubble

F_stall

| W | icode |  | valE | valM |  | dstE | dstM |  |
|---|---|---|---|---|---|---|---|---|

| M | icode | Cnd |  | valE | valA |  | dstE | dstM |  |
|---|---|---|---|---|---|---|---|---|---|

| E | icode | ifun |  | valC | valA | valB | dstE | dstM | srcA | srcB |
|---|---|---|---|---|---|---|---|---|---|---|

| D | icode | ifun |  | rA | rB | valC | valP |  |
|---|---|---|---|---|---|---|---|---|

| F |  |  | predPC |  |  |
|---|---|---|---|---|---|

## Control Cases

- Detection

| Condition | Trigger |
|---|---|
| Processing ret | IRET in { D_icode, E_icode, M_icode } |
| Load/Use Hazard | E_icode in { IMRMOVL, IPOPL } && E_dstM in { d_srcA, d_srcB } |
| Mispredicted Branch | E_icode = IJXX & !e_Cnd |

- Action

| Condition | F | D | E | M | W |
|---|---|---|---|---|---|
| Processing ret | stall | bubble | normal | normal | normal |
| Load/Use Hazard | stall | stall | bubble | normal | normal |
| Mispredicted Branch | normal | bubble | bubble | normal | normal |

## Implementing Pipeline Control

- Combinational logic generates pipeline control signals
- Action occurs at start of following cycle

## Initial Version of Pipeline Control

```
bool F_stall =
    # Conditions for a load/use hazard
    E_icode in { IMRMOVL, IPOPL } &&
    E_dstM in { d_srcA, d_srcB } ||
    # Stalling at fetch
    while ret passes through pipeline
    IRET in { D_icode, E_icode, M_icode };
```

```
bool D_stall =
    # Conditions for a load/use hazard
    E_icode in { IMRMOVL, IPOPL } &&
    E_dstM in { d_srcA, d_srcB };
```

## Initial Version of Pipeline Control

```
bool D_bubble =
    # Mispredicted branch
    (E_icode == IJXX && !e_Bch) ||
    # Stalling at fetch
    while ret passes through pipeline
    IRET in { D_icode, E_icode, M_icode };
```

```
bool E_bubble =
    # Mispredicted branch
    (E_icode == IJXX && !e_Bch) ||
    # Load/use hazard
    E_icode in { IMRMOVL, IPOPL } &&
    E_dstM in { d_srcA, d_srcB };
```

