# 5.5 Yacc: LALR(1) PARSING GENERATOR

```
main ( )
{ return yyparse( );
}
int yylex(void)
{
  int c;
  while( ( c = getchar( ) ) == ‘ ’);
  /*eliminates blanks */
  if ( isdigit(c) ) {
    unget (c,stdin) ;
    scanf (“%d”,&yylval1) ;
    return (NUMBER ) ;
  }
  if (c== ‘\n’) return 0;
  /* makes the parse stop */
  return ( c ) ;
}
```

![](bbox=[0.76, 0.67, 1.0, 0.99])

![](bbox=[0.0, 0.91, 0.09, 1.0])