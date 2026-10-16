# 相应的 LEX 源程序 框架

```
/* 说明部分 */
%{
#include <stdio.h>
/* C语言描述的标识符常量的定义，如 LT、LE、EQ、NE、GT、
    GE、IF、THEN、ELSE、ID、NUMBER、RELOP */
extern yylval;
%}
    /* 正规定义式 */
delim  [ \t\n]
ws     {delim}+
letter [A-Za-z]
digit  [0-9]
id     {letter}({letter}|{digit})*
num    {digit}+(\.{digit}+)?(E[+\-]?{digit}+)?
%%
```