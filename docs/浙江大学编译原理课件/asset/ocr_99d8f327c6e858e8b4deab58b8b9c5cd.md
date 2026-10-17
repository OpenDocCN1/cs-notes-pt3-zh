# 6.1.1 Attribute grammars

# Example 6.2 :

exp → exp + term | exp-term|term
term → term*factor | factor
factor → (exp)|number

| Grammar Rule | Semantic Rules |
|---|---|
| exp1→ exp2 + term | exp1.val = exp2.val + term.val |
| exp1→ exp2 - term | exp1.val = exp2.val - term.val |
| exp1→ term | exp1.val = term.val |
| term1→ term2*factor | term1.val = term2.val*factor.val |
| term→ factor | term.val = factor.val |
| factor→ (exp) | factor.val = exp.val |
| factor→number | factor.val = number.val |