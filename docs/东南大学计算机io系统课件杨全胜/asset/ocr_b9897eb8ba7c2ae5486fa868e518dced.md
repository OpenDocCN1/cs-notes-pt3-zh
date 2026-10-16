# 1.6.3 Stack Memory Addressing Modes

# PUSH operation

+   - Whenever a word of data is pushed onto the stack, the high-order 8 bit are placed in the location addressed by SP-1; The low-order 8 bit are placed in the location addressed by SP-2.

+   - The SP is then decremented by 2 so that the next word of data is stored in the next available stack memory location.

# POP operation

+   - Whenever a word of data is popped from the stack, the low-order 8 bit are removed from the location addressed by SP. The high-order 8 bit are removed from the location addressed by SP+1.

+   - The SP is then incremented by 2.