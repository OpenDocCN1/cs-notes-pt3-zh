# Nonregular languages

+   - Finite automata has finite states, so there are some languages that FA can’t recognize.
+     - E.g. $B = \{0^n1^n | n \geqq 0\}$
+   - To prove a language is not a nonregular, we state a property that a regular language possesses.
+   - The pumping lemma for regular languages:
+     - All strings in a regular language can be “pumped” if they are at least as long as a certain special value, called the pumping length.
+   - This lemma means that such string contains a section that can be repeated any number of times with the resulting string remaining in the language.