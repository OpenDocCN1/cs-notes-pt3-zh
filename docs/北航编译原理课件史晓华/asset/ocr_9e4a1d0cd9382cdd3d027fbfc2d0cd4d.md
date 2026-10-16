# ★ 为什么对符号、符号串、符号串集合以及它们的运算感兴趣？

若 A 为某语言的基本字符集（把字符看作符号）

$A=\{a,b,\ldots,z,0,1,\ldots,9,+,-,\times,\_,/,(),=,\ldots\}$

B 为单词集（单词是符号串）

$B=\{begin,end,if,then,else,for,\ldots,\langle\text{标识符}\rangle,\langle\text{常量}\rangle,\ldots\}$

则 $B\subset A^*$。

> （把单词看作符号，句子便是符号串）

语言的句子是定义在 B 上的符号串。若令 C 为句子集合，则 $C\subset B^*$，程序 $∈ C$。