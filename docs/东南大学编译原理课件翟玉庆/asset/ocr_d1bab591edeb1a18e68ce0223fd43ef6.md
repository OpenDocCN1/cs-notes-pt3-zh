# CHAPTER 3 LEXICAL ANALYSIS

# Section 8 Design of a lexical analyzer generator

# 3、 Lex

# d) Lex specification

# (2)Translation Rules

p₁ {action₁} /*p—pattern(Regular exp) */

...

pₙ {actionₙ}

e.g {if} {return(IF);}

{id} {yylval=install_id();return(ID);}