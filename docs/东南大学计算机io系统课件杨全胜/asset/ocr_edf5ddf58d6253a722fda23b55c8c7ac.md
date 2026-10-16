# 2.6.6 String Instructions

# String Data Transfer Instructions

# STOS Instruction

Stores AL, AX or EAX at the extra segment memory location addressed by the (E)DI register.

| Assemble Language | Operation |
|---|---| 
| STOSB | ES:[DI]=AL; if (DF=0) DI=DI+1 else DI=DI-1 |
| STOSW | ES:[DI]=AX; if (DF=0) DI=DI+2 else DI=DI-2 |
| STOSD | ES:[DI]=EAX; if (DF=0) DI=DI+4 else DI=DI-4 |

# STOS with a REP prefix

+   - REP prefix cause (E)CX decrement by 1 each time string instruct executes. Then string instruction repeat. If (E)CX reaches a value of 0, the instruction terminate and the program continues with the next sequential instruction.