# # 5.5 Yacc: LALR(1) PARSING GENERATOR

•In the third section, yyparse is declared to return an integer value, which is 0 if the parse succeeeds, and 1 if it does not.

+   ➤The yyparse procedure calls a scanner procedure( yylex.)

+   ➤Yacc expects the end of input to be signaled by a return of the null value 0 by yylex.

+   ➤ yyerror prints an error message when an error is encountered during the parse.