# 改造后文法：

Z->A
A->aA’A’’’
A’->B|C
A’’->d|e
A’’’->A’’ A’’’| ε
B->bBC|f
C->c

First(Z)={a}
First(A)={a}
First(A’ )={b,f,c}
First(A’’)={d,e}
First(A’’’ )={d,e, ε}
First(B)={b,f}
First(C)={c}