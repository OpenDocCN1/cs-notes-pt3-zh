
e.g. Construct a right-linear grammar for the following DFA M = ({A,B,C,D},{0,1},f,A,{B})

![](img/353f619caa6c5715591f2105bdfa2865_150_0.png)

Answer: RG = ({A,B,C,D},{0,1},P,A)

```
A → 0B | 1D | 0
B → 1C | 0D
C → 0B | 1D | 0
D → 0D | 1D
```

L(RG) = L(M) = 0(10)*

![](img/353f619caa6c5715591f2105bdfa2865_151_0.png)

## CHAPTER 3 LEXICAL ANALYSIS

### Section 8 Design of a lexical analyzer generator

- 1. Lexical analyzer generator

  A software tool that automatically constructs a lexical analyzer from related language specification.

- 2. Typical lexical analyzer generator

  Lex

- 3. Lex

  - a) Lexical analyzer generating tool

    Lex compiler

  - b) Input specification

    Lex language program

  - c) The process that creates a lexical analyzer with Lex

    ![](img/353f619caa6c5715591f2105bdfa2865_154_0.png)

  - d) Lex specification

    A Lex program consists of three parts:

    - declaration
    - %%
    - translation rules
    - %%
    - auxiliary procedures

    - (1) Declaration

      Include declarations of variables, manifest constants and regular definitions.

      Notes: A manifest constant is an identifier that is declared to represent a constant.

    - (2) Translation Rules

      ```
      p₁ {action₁} /* p — pattern (Regular exp) */
      ...
      pₙ {actionₙ}
      ```

      e.g.

      ```
      {if} {return(IF);}
      {id} {yylval=install_id(); return(ID);}
      ```

    - (3) Auxiliary procedures

      ```
      install_id() {
        /* procedure to install the lexeme, whose
      first character is pointed to by yytext and whose
      length is yyleng, into the symbol table and return
      a pointer thereto*/
      }
      ```

      Notes: The auxiliary procedures can be compiled separately and loaded with the lexical analyzer.

    ```
    %{ /* this part is copied literally to the generated C code */
    #define IF 5
    #define ID 12
    #define INTEGER 13
    #define REAL 14
    %}
    delim    [ \t\n]+
    letter   [A-Za-z]
    digit    [0-9]
    id       {letter}({letter}|{digit})*
    integer  {digit}+
    real     {digit}+\.{(digit)+}?|({digit}+)?\.{digit}+
    %%
    {delim}  { /* no action and no return */ }
    if       {return IF;}
    {id}     {yylval = install_id(); return ID;}
    {real}   {yylval = convert_real(); return REAL;}
    {integer}{yylval = convert_int(); return INTEGER;}
    %%
    install_id() { ... procedure to enter or lookup in the symbol table the string pointed to by yytext with length yyleng ...}
    ```

    ```
    %{
    /* a lex program that adds line numbers to lines of text,
    printing the new text to the standard output */
    #include <stdio.h>
    int lineno = 1;
    %}
    line	.*\n
    %%
    {line}	{printf("%5d %s", lineno++, yytext);}
    %%
    main()
    { yylex(); return 0;}
    ```

  - e) Model of Lex compiler

    ![](img/353f619caa6c5715591f2105bdfa2865_162_0.png)

## CHAPTER 4 Syntax Analysis

### Section 0 Approaches to Implement a Syntax Analyzer

- 1. The syntax description of programming language constructs

  - Context-free grammars
  - BNF (Backus Naur Form) notation

Notes: Grammars offer significant advantages to both language designers and compiler writers.

- 2. Why a grammar is usually used to describe the syntax of a programming language?

  - A grammar gives a precise, yet easy-to-understand, syntactic specification of a programming language.
  - From certain classes of grammar we can automatically construct an efficient parser that determines if a source program is syntactically well formed.
