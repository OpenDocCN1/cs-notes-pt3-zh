# 相应的 LEX 源程序 框架

```
/* 规则部分 */
{ws}    {/* 没有动作，也不返回 */}
if      { return(IF); }
then    { return(THEN); }
else    { return(ELSE); }
{id}    { yylval=install_id(); return(ID); }
{num}   { yylval=install_num();
          return(NUMBER); }
"<"    { yylval=LT; return(RELOP); }
"<="   { yylval=LE; return(RELOP); }
"="    { yylval=EQ; return(RELOP); }
"<>"   { yylval=NE; return(RELOP); }
">"    { yylval=GT; return(RELOP); }
">="   { yylval=GE; return(RELOP); }
%%
```

如果没有return语句，则，处理整个输入之后才会返回！！