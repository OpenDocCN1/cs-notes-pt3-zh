# 正则表达式与3型文法等价

例如：

正则表达式： ba*

a(a|b)*

3型文法： Z ::= Za|b

Z ::= Za|Zb|a

例：

# 3型文法

# 正则表达式

S ::= aS|aB

B ::= bC

C ::= aC|a

aS|aba*a

ba*a

a*a

a*aba*a