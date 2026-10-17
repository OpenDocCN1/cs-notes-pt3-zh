# 6.3 The symbol table

+   - **Semantic checks** refer to properties of identifiers in the program -- their scope or type
+   - Need an environment to store the information about identifiers = **symbol table**
+   - Each entry in the symbol table contains
+     - the name of an identifier
+     - additional information: its kind, its type, if it is constant, ...

| NAME | KIND | TYPE | ATTRIBUTES |
|---|---|---|---|
| `foo` | fun | `int x int → bool` | extern |
| `m` | arg | int | |
| `n` | arg | int | const |
| `tmp` | var | bool | const |