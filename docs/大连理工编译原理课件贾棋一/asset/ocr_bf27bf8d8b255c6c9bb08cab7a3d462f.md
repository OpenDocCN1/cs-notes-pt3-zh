# 3.5 LR分析器

例 为语言 $L=\{a^m b^n \mid n>m\geq 0\}$ 写三个文法，它们分别是LR(1)的、二义的和非二义且非LR(1)的

+   - **LR(1)文法：** $S\to AB$　$A\to aAa b\mid\varepsilon$　$B\to Bb\mid b$

+   - **非二义且非LR(1)的文法：** $S\to aSb\mid B$　$B\to Bb\mid b$

+   - **二义的文法：** $S\to aSb\mid Sb\mid b$

![](bbox=[0.571, 0.689, 0.953, 0.999])