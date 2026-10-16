+   %{
+   • #include <stdio.h>
+   • #include "y.tab.h"
+   • #define ID 1
+   • #define INT 2
+   • #define EXP 3
+   • #define MULTI 4
+   • #define COLON 5
+   • #define EQ 6
+   • #define NE 7
+   • #define LE 8
+   • #define GE 9
+   • #define LT 10
+   • #define GT 11
+   • #define PLUS 12
+   • #define MINUS 13
+   • #define RDIV 14
+   • #define COMMA 15
+   • #define SEMIC 16
+   • #define RELOP 17
+   • #define ASSGIN 18
+   • int line_no = 1; %}

+   • delim [\t\n]
+   • ws [delim]+
+   • letter [a-zA-Z]
+   • digit [0-9]
+   • id {letter}({letter}|{digit})*
+   • number {digit}+
+   • %%
+   • {ws} ;
+   • begin return(BEGIN);
+   • end return(END);
+   • if return(IF);
+   • then return(THEN);
+   • else return(ELSE);
+   • do return(DO);
+   • program return(PROGRAM);
+   • {id} {yyval = install_id(); return(ID);}
+   • {number} {yyval = install_num(); return(INT);}