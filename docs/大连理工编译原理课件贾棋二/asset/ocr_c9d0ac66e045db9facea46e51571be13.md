# 3.7 分析器的生成器

# 例——翻译规则部分

```
line : expr '\n'  {printf("%d\n", $1);}
;
expr : expr '+' term  {$$ = $1+$3;}
| term
;
term : term '*' factor  {$$ = $1 * $3;}
| factor
;
factor : '(' expr ')'  {$$ = $2;}
| DIGIT
;
%%
```

```
E->E + T | T
T->T * F | F
F->(E) | digit
```