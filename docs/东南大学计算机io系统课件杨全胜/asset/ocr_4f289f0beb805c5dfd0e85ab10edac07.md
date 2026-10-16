# 2.4 Assembly Language Source Code

# Using Simplified Segment Directives

# .MODEL

```
`.MODEL memorymodel [[, langtype]] [[, stackoption]]`
```

+   - Initializes the program memory model.
+   - You must place `.MODEL` in your source file before any other simplified segment directive.
+   - The *memorymodel* can be **TINY, SMALL, COMPACT, MEDIUM, LARGE, HUGE,** or **FLAT**. If you are writing an assembler routine for a high-level language, this option should match the memory model used by the compiler or interpreter.