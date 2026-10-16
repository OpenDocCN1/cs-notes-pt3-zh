# LALR(1) 分析程序和LR(1) 分析程序的比较

■ LALR（1）分析程序对符号串c d c d的分析过程

| 步骤 | 栈 | 输入 | 分析动作 |
|---:|---|---|---|
| 0 | 0 | c d c d$ | shift |
| 1 | 0c36 | d c d$ | shift |
| 2 | 0c36d47 | c d$ | reduce by C→d |
| 3 | 0c36C89 | c d$ | reduce by C→CC |
| 4 | 0C2 | c d$ | shift |
| 5 | 0C2c36 | d$ | shift |
| 6 | 0C2c36d47 | $ | reduce by C→d |
| 7 | 0C2c36C89 | $ | reduce by C→CC |
| 8 | 0C2C5 | $ | reduce by S→CC |
| 9 | 0S1 | $ | accept |