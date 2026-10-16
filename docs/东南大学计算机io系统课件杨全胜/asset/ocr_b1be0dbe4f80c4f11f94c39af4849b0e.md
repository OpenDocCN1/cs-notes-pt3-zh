# 2.6.6 String Instructions

# String Data Transfer Instructions

# MOVS Instruction

+   - Transfers a byte, word, or doubleword from the data segment location addressed by (E)SI to the extra segment location addressed by (E)DI.
+   - MOVS can also with a REP prefix.

| Assemble Language | Operation |
|---|---|
| MOVSB | ES:[DI]=DS:[SI]; if (DF=0) {SI=SI+1; DI=DI+1} else {SI=SI-1; DI=DI-1} |
| MOVSW | ES:[DI]=DS:[SI]; if (DF=0) {SI=SI+2; DI=DI+2} else {SI=SI-2; DI=DI-2} |
| STOSD | ES:[DI]=DS:[SI]; if (DF=0) {SI=SI+4; DI=DI+4} else {SI=SI-4; DI=DI-4} |