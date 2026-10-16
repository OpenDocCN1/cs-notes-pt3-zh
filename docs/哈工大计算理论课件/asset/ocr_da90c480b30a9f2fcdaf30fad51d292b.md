# Designing context-free grammars

+   - Technique two:
+     - Break into simpler pieces:
+     - Many CFLs are the union of simple CFLs. So break into simpler pieces, then construct individual grammars for each piece. Merge them into a grammar for the original language by combining their rule and then adding the new rule
+   
+       $S \rightarrow S_1 | S_2 | ... | S_k$
+     - where $S_i$ are the start variables for the individual grammars.