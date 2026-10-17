# 3.2.3 Derivations and the language defined by a grammar

+   Example : \( A \rightarrow (A) A \mid \varepsilon \)

This grammar generates the strings of all "balanced parentheses."

For example, the string \((( ) (( ))) ( )\)

\( A \Rightarrow (A) A \Rightarrow (A)(A)A \Rightarrow (A)(A) \Rightarrow (A)() \Rightarrow ((A)A)() \Rightarrow ( ()A)() \Rightarrow ( () (A)A ) () \Rightarrow (( )(A ))() \Rightarrow (( )((A)A))() \Rightarrow (( )(( )A))() \Rightarrow (( )(( )))() \)