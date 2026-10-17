# # 3.1 上下文无关文法

# ## 3.1.2 推导

把产生式看成重写规则，把符号串中的非终结符用其产生式右部的串来代替。

例  
\( E \to E+E \mid E*E \mid (E) \mid -E \mid id \)  
\( E \Rightarrow -E \Rightarrow -(E) \Rightarrow -(E+E) \Rightarrow -(id+E) \Rightarrow -(id+id) \)

记号  
\( S \Rightarrow^* \alpha \, S \Rightarrow^+ w \)

概念  
句型、句子、上下文无关语言、等价的文法