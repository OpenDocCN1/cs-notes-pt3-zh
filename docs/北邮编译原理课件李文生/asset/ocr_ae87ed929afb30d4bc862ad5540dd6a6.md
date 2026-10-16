# LR(1)分析程序对符号串ccd的分析过程

| 步骤 | 栈 | 输入 | 分析动作 |
| --- | --- | --- | --- |
| 0 | 0 | ccd$ | shift |
| 1 | 0c3 | cd$ | shift |
| 2 | 0c3c3 | d$ | shift |
| 3 | 0c3c3d4 | $ | error |

# LALR(1)分析程序对符号串ccd的分析过程

| 步骤 | 栈 | 输入 | 分析动作 |
| --- | --- | --- | --- |
| 0 | 0 | ccd$ | shift |
| 1 | 0c36 | cd$ | shift |
| 2 | 0c36c36 | d$ | shift |
| 3 | 0c36c36d47 | $ | reduce by C→d |
| 4 | 0c36c36C89 | $ | reduce by C→cC |
| 5 | 0c36C89 | $ | reduce by C→cC |
| 6 | 0C2 | $ | error |