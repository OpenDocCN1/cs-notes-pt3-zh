# # 无符号数的右线性文法的状态转换图

num → digit num1
num1 → digit num1 | . num2 | E num4 | ε
num2 → digit num3
num3 → digit num3 | E num4 | ε
num4 → + digits | - digits | digit num5
digits → digit num5
num5 → digit num5 | ε

![](bbox=[0.018, 0.575, 0.982, 0.925])