# Regular expressions

+   - Elemental objects in a programming language is tokens.
+   - Variable names and constants in programming language are tokens, they can be described with regular expressions.
+   - A numerical constant can be described as a member of the language
+     - (+ ∪ - ∪ ε) (D⁺ ∪ D⁺.D* ∪ D*.D⁺)
+       where D = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9}
+   - Once the syntax of the tokens of the programming language have been described with regular expressions, automatic systems can generate the lexical analyzer, which is part of a compiler processing the input program.