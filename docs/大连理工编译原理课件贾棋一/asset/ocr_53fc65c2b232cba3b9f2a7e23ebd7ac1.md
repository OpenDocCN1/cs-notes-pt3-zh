# 3.6 二义文法的应用

# 二义文法的特点：

+   二义文法决不是LR文法

+   简洁、自然

二义文法： \( E \rightarrow E + E \mid E * E \mid (E) \mid \text{id} \)
非二义的文法：
\( E \rightarrow E + T \mid T \)
\( T \rightarrow T * F \mid F \)
\( F \rightarrow (E) \mid \text{id} \)