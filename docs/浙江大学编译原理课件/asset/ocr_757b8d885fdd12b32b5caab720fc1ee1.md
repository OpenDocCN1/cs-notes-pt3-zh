# # 4.5 Error Recovery in Top-Down Parsers

+   - The basic mechanism of panic mode:
+     - A set of **synchronizing tokens** are provided to each recursive procedure;
+     - If an error is encountered, the parser scans ahead, throwing away tokens until one of the synchronized tokens is seen in the input, and then parsing is resumed.