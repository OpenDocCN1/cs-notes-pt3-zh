# 例：

+   - E → T E’
+   - E’ → + T E’ | ε
+   - T → F T’
+   - T’ → * F T’ | ε
+   - F → id | ( E )

| 文法符号 | First集 | Follow集 |
|---|---|---|
| E | { id, ( } | { }, # } |
| E’ | { +, ε } | { }, # } |
| T | { id, ( } | { +, ), # } |
| T’ | { *, ε } | { +, ), # } |
| F | { id, ( } | { *, +, ), # } |

Predict( T’ →*FT’ ) = first(*FT’ ) = { * }

Predict( T’ → ε ) = follow(T’ ) = { + , ), # }

Predict( F →id ) = first(id) = { id }

Predict( F →(E) ) = first((E)) = { ( }