# 3.2.3 Derivations and the language defined by a grammar

+   - this turns the semicolon into a `statement terminator` rather than a **statement separator**;
+   - allow statement sequences to be empty, but retain the semicolon as a statement separator.

```
stmt-sequence → nonempty-stmt-sequence | ε
nonempty-stmt-sequence → stmt; nonempty-stmt-sequence | stmt
stmt → s
```

+   - care must be taken in the placement of the ε-production when constructing optional structures

![](bbox=[0.788, 0.668, 0.999, 0.999])

![](bbox=[0.0, 0.909, 0.081, 0.999])