
## CHAPTER 4 SYNTAX ANALYSIS

### Section 5 LR parsers

#### 5. The LR Parsing Model

**Note:**

1. The driver program is the same for all LR parsers; only the parsing table changes from one parser to another.
2. The parsing program reads characters from an input buffer one at a time.
3. $S_i$ is a state; each state symbol summarizes the information contained in the stack below it.
4. Each state symbol summarizes the information contained in the stack.
5. The current input symbol is used to index the parsing table and determine the shift-reduce parsing decision.
6. In an implementation, the grammar symbols need not appear on the stack.

#### 6. The Parsing Table

- **Action**: a parsing action function.
  - $Action[S,a]$: S represents the state currently on top of the stack, and a represents the current input symbol. So $Action[S,a]$ means the parsing action for S and a.
- **Shift**:
  - The next input symbol is shifted onto the top of the stack.
  - Shift S, where S is a state.
- **Reduce**:
  - The parser knows the right end of the handle is at the top of the stack, locates the left end of the handle within the stack, and decides what non-terminal to replace the handle. Reduce by a grammar production $A \to \alpha$.
- **Accept**:
  - The parser announces successful completion of parsing.
- **Error**:
  - The parser discovers that a syntax error has occurred and calls an error recovery routine.
- **Action conflict**:
  - **Shift/reduce conflict**
    - Cannot decide whether to shift or to reduce.
  - **Reduce/reduce conflict**
    - Cannot decide which of several reductions to make.

**Note:** An ambiguous grammar can cause conflicts and can never be LR, e.g., `If_stmt` syntax (`if expr then stmt [else stmt]`).

#### 7. The Algorithm

- The next move of the parser is determined by reading the current input symbol $a$ and the state $S$ on top of the stack, and then consulting the parsing action table entry $action[S,a]$.
- If $action[S_m,a_i]=shift\ S'$, the parser executes a shift move, enters $S'$ into the stack, and the next input symbol $a_{i+1}$ becomes the current symbol.
- If $action[S_m,a_i]=reduce\ A\to\alpha$, then the parser executes a reduce move. If the length of $\alpha$ is $\gamma$, then delete $\gamma$ states from the stack, so that the state at the top of the stack is $S_{m-\gamma}$. Push the state $S'=GOTO[S_{m-\gamma},A]$ and non-terminal A into the stack. The input symbol does not change.
- If $action[S_m,a_i]=accept$, parsing is completed.
- If $action[S_m,a_i]=error$, the parser has discovered an error and calls an error recovery routine.

E.g. the parsing action and goto functions of an LR parsing table for the following grammar:

$E \to E + T$  
$E \to T$  
$T \to T * F$  
$T \to F$  
$F \to (E)$  
$F \to i$

| state | i | + | * | ( | ) | $ | E | T | F |
|---|---|---|---|---|---|---|---|---|---|
| 0 | S₅ |  |  | S₄ |  |  | 1 | 2 | 3 |
| 1 |  | S₆ |  |  |  | accept |  |  |  |
| 2 |  | r₂ | S₇ |  | r₂ | r₂ |  |  |  |
| 3 |  | r₄ | r₄ |  | r₄ | r₄ |  |  |  |
| 4 | S₅ |  |  | S₄ |  |  | 8 | 2 | 3 |
| 5 |  | r₆ | r₆ |  | r₆ | r₆ |  |  |  |
| 6 | S₅ |  |  | S₄ |  |  |  | 9 | 3 |
| 7 | S₅ |  |  | S₄ |  |  |  |  | 10 |
| 8 |  | S₆ |  |  | S₁₁ |  |  |  |  |
| 9 |  | r₁ | S₇ |  | r₁ | r₁ |  |  |  |
| 10 |  | r₃ | r₃ |  | r₃ | r₃ |  |  |  |
| 11 |  | r₅ | r₅ |  | r₅ | r₅ |  |  |  |
