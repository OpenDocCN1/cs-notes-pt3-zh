# Packaging commonly used functions

+   - Solution: static libraries (.a archive files)
+     - concatenate related relocatable object files into a single file with an index (called an archive)
+     - enhance linker so that it tries to resolve unresolved external references by looking for the symbols in one or more archives
+     - If an archive member file resolves reference, link into executable