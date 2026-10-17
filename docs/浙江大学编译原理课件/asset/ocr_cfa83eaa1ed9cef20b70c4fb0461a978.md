# 3.2.3 Derivations and the language defined by a grammar

+   • Example : Consider the following grammar G for a sequence of statements:
+   ```
+   stmt-sequence → stmt ; stmt-sequence | stmt
+   stmt → s
+   ```

+   • This grammar generates sequences of one or more statements separated by semicolons
+   ```
+   L(G)= { s, s;s, s;s;s... }
+   ```