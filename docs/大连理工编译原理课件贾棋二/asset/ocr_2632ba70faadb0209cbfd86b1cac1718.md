# # 3.7 分析器的生成器

# ## 例——声明部分

%{
#include <ctype.h>
%}
%token DIGIT
%%

/* 常量、变量的声明*/

```
E->E + T | T
T->T * F | F
F->(E) | digit
```