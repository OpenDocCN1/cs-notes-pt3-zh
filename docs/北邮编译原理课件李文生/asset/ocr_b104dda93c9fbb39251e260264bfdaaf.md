# 四、YACC内部名称

| YACC内部名称 | 说明 |
|---|---|
| y.tab.c | YACC输出文件名 |
| y.tab.h | YACC生成的头文件，包含有记号定义 |
| yyparse | YACC分析程序 |
| yylval | 栈中当前记号的值 |
| yyerror | 由YACC使用的用户定义的错误信息打印程序 |
| error | YACC错误伪记号 |
| yyerrork | 在错误处理之后，使分析程序回到正常操作方式的程序 |
| yychar | 变量，记录导致错误的先行记号 |
| YYSTYPE | 定义分析栈值类型的预处理器符号 |
| yydebug | 变量，当由用户设置为1时，生成有关分析动作的运行信息 |