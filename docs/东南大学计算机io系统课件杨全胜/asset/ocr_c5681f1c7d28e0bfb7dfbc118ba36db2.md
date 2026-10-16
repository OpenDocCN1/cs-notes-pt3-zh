# 2.6.1 Data Movement Instructions

# Miscellaneous data transfer instructions

# MOVSX and MOVZX Instruction

Example:
if (CL)=0ABH,
MOVSX AX, CL
    after execution (AX)=0FFABH   ; Sign-extend
MOVZX AX, CL
    after execution (AX)=00ABH    ; Zero-extend
if (DATA) = 78ADH
MOVSX EAX, DATA
    after execution (AX)=000078ADH ; Sign-extend
MOVZX EAX, DATA
    after execution (AX)=000087ADH ; Zero-extend