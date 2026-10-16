# 2.6.2 Arithmetic Instructions

+   - Multiplication and Division
+     - Unsigned Division
+       - DIV SRC
+     - Signed Division
+       - IDIV SRC

| Symbolic | Operation |
|---|---|
| DIV/IDIV reg/mem8 | AX divided by reg/mem8
AL←Quotient, AH←Remainder |
| DIV/IDIV reg/mem16 | DX:AX divided by reg/mem16
AX←Quotient, DX←Remainder |
| DIV/IDIV reg/mem32 | EDX:EAX divided by reg/mem32
EAX←Quotient, EDX←Remainder |