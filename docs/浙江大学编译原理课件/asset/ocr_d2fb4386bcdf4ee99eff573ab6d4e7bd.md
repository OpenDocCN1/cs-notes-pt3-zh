# # 3.2.2 Specification of context-free grammar rules

+   - The choice operation given by the vertical bar metasymbol is also not necessary in grammar rules.
+     For example, simple expression grammar could be written as follows:
+     ```
+     exp → exp op exp
+     exp → ( exp )
+     exp → number
+     op → +
+     op → -
+     op → *
+     ```