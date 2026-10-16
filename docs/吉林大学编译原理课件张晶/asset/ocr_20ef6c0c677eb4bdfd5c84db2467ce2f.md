Predict(S→AB ) = { a,b,# }
Predict(S→ bC ) = { b }
Predict( A → ε) = { a , c , # }
Predict( A→b ) = { b }
Predict( B → ε) = { # }
Predict( B → aD ) = {a }
Predict( C →AD ) = {a,b,c }
Predict( C →b) = { b }
由于： Predict(S→AB ) ∩Predict(S→ bC ) = { b }
        Predict( C →AD ) ∩Predict( C →b) = { b }
所以该文法不是递归下降文法。

| 文法符号 | First集 | Follow集 |
|---|---|---|
| S | { a, b, ε } | { # } |
| A | { b, ε } | { a, c, # } |
| B | { a, ε } | { # } |
| C | { a, b, c } | { # } |
| D | { a, c } | { # } |