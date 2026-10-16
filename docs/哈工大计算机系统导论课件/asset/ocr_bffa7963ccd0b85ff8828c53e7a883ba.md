# 加、减、乘、除指令汇总

| | 加法 | 减法 | 乘法 | 除法 |
|---|---|---|---|---|
| 无符号二进制数 | ADD/ADC | SUB/SBB | MUL | DIV |
| 有符号二进制数 | ADD/ADC | SUB/SBB | IMUL | CBW、CWD、CDQ、CQQ IDIV |
| 非压缩BCD码 | ADD/ADC
AAA | SUB/SBB
AAS | MUL
AAM | AAD
DIV |
| 压缩BCD码 | ADD/ADC
DAA | SUB/SBB
DAS |  |  |