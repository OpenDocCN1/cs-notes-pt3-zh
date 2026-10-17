# # 5.4.2 The LR(1) Parsing Algorithm

# ## The General LR(1) parsing algorithm :

Let s be the current state (a the top of the parsing stack). Then actions are defined as follows:

+   1. If state s: any LR(l ) item of the form [A→α·Xβ,a], X is a terminal, and X is the next token in the input string

+   2. If state s : the complete LR(1) item [A→ α ·,a] , the next token: in the input string is a

+   3. If the next input token is such that neither of the above two cases applies, an error is declared.