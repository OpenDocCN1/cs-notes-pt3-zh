# 2.6.4 Jump Instructions

# Conditional Jump (Jcc)

| Assembly | Operation | Tested Condition |
|---|---|---|
| JC | Jump if Carry | CF=1 |
| JNC | Jump if no Carry | CF=0 |
| JZ/JE | Jump if equal or Zero | ZF=1 |
| JNZ/JNE | Jump if no equal or no Zero | ZF=0 |
| JS | Jump if sign (negative) | SF=1 |
| JNS | Jump if no sign (positive) | SF=0 |
| JO | Jump if overflow | OF=1 |
| JNO | Jump if no overflow | OF=0 |
| JP/JPE | Jump if parity even | PF=1 |
| JNP/JPO | Jump if parity odd | PF=0 |
| JCXZ | Jump if CX is Zoro | CX=0 |
| JECXZ | Jump if ECX is Zero | ECX=0 |