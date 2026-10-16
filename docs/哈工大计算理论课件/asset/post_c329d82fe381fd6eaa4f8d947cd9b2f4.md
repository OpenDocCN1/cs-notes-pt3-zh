
## Context-free Grammars

Example 4: a context-free grammar $G_4=(V, \Sigma,R, <EXPR>)$ where
$V = \{<EXPR>, <TERM>, <FACTOR>\}$,
$\Sigma = \{A, +, \times, (, )\}$,
The rules are
$<EXPR> \rightarrow <EXPR> + <TERM> \mid <TERM>$
$<TERM> \rightarrow <TERM> \times <FACTOR> \mid <FACTOR>$
$<FACTOR> \rightarrow (<EXPR>) \mid a$

## Context-free Grammars

+   a + a × a and (a + a) × a can be generated with grammar $G_4$

![](img/505b35cb28b35d38fc29ccba74c23087_165_0.png)

![](img/505b35cb28b35d38fc29ccba74c23087_165_1.png)

## Designing context-free grammars

- For we are more accustomed to programming a machine for specific tasks than we are to describing languages with grammars. So designing a CFG is even harder than a FA.

## Designing context-free grammars

- **Technique one:**
  - To remember the substring:
  - Certain CFLs contain strings with two substrings that require the machine to remember an unbounded amount of information about one of the substring s, in order to verify the corresponding properly to the other substring.
  - Then you can construct a CFG by using a rule of the form
    $R \to uRv$
  - E.g. $\{0^n1^n \mid n \ge 0\}$          $S_1 \to 0S_1 1 \mid \varepsilon$
    here CFG remembers the number of 0s in order to verify that it equals the number of 1s.

## Designing context-free grammars

- Technique two:
  - Break into simpler pieces:
  - Many CFLs are the union of simple CFLs. So break into simpler pieces, then construct individual grammars for each piece. Merge them into a grammar for the original language by combining their rule and then adding the new rule
    $S \rightarrow S_1 | S_2 | ... | S_k$
  - where $S_i$ are the start variables for the individual grammars.

## Designing context-free grammars

- Example:
  - The language {0^n1^n | n ≥ 0} ∪ {1^n0^n | n ≥ 0}
  - For {0^n1^n | n ≥ 0}
    S₁ → 0S₁1 | ε
  - For {1^n0^n | n ≥ 0}
    S₂ → 1S₂0 | ε
  - So adding the new rule, we get
    S → S₁ | S₂
    S₁ → 0S₁1 | ε
    S₂ → 1S₂0 | ε

## Designing context-free grammars

### Technique three:

- For regular language, construct DFA first
- Then, we convert the DFA to a CFG
- Make a variable $R_i$ for each state $q_i$ of the DFA.
- Add the rule $R_i \to aR_j$ to the CFG if $\delta(q_i,a)=q_j$
- Add the rule $R_i \to \varepsilon$ if $q_i$ is an accept state.
- Make $R_0$ the start variable, where $q_0$ is the start state of the DFA

## Designing context-free grammars

- Technique four:
  - Recursive structure.
  - E.g. Example 4, any time the symbol *a* appear, an entire parenthesized expression might appear recursively instead.
  - To achieve this affect, place the variable symbol generating the structure in the location of the rules corresponding to where that structure may recursively appear.

## Designing context-free grammars

- On class exercise:
- Given that Σ=(0,1)
- {w| w starts and ends with the same symbol}

## Designing context-free grammars

- On class exercise:
- {w| w contains at least three 1s }

## Ambiguity

In some grammar, the same string can be generated in several different way (have several different parse trees), so have several different meanings.

Note: two parse trees, not two ways to derive.

If a grammar generates the same string in several different way, we say that the string is derived ambiguously in that grammar.

## Ambiguity

E.g.
<EXPR> → <EXPR> + <EXPR> | <EXPR> × <EXPR> | (<EXPR>) | a

to generate a + a × a

![](img/505b35cb28b35d38fc29ccba74c23087_175_0.png)

![](img/505b35cb28b35d38fc29ccba74c23087_175_1.png)

This grammar doesn’t capture the usual precedence relations, but Example 4 does.

## Ambiguity

- E.g
  - Example 2 is an ambiguous grammar too.
  - the girl touches the boy with the flower is ambiguous.
