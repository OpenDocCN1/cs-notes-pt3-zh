# 3.7 分析器的生成器

```
%{
# include <ctype.h>
# include <stdio.h>
# define YYSTYPE double /* 将栈定义为double 类型 */
%}
```

```
%token NUMBER
%left '+' '-'
%left '*' '/'
%right UMINUS
```

```
lines→ lines expr '\n' | lines '\n' | e
E→ E + E | E - E | E * E | E / E | (E) | -E
number
```