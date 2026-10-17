# 3.7 Syntax of the TINY language

# figure 3.6: Grammar of the TINY language in BNF

program → stmt-sequence

stmt-sequence→ stmt-sequence; statement | statement

statement → if-stmt | repeat-stmt | assign-stmt | read-stmt | write-stmt

if-stmt→ if exp then stmt-sequence end

| if exp then stmt-sequence else stmt-sequence end

repeat-stmt→ repeat stmt-sequence until exp

assign-stmt→ identifier := exp

read-stmt → read identifier

write-stmt → write exp

exp → simple-exp comparison-op simple-exp | simple-exp

comparison-op → < | =

simple-exp → simple-exp addop term | term

addop → +|-

term → term mulop factor factor | factor

mulop → */l

factor → (exp) |number |identifier

![](bbox=[0.598, 0.648, 0.992, 0.934])