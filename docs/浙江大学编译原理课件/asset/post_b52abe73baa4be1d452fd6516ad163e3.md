
## 5.1 OVERVIEW OF BOTTOM-UP PARSING

Right-most derivation — backward.  
Start with the tokens; end with the start symbol.

```
(1+2+(3+4))+5 ⇐
(E+2+(3+4))+5 ⇐
(S+2+(3+4))+5 ⇐
(S+E+(3+4))+5 ⇐
(S+(3+4))+5 ⇐
(S+(E+4))+5 ⇐
(S+(S+4))+5 ⇐
(S+(S+E))+5 ⇐
(S+(S))+5 ⇐
(S+E)+5 ⇐
(S)+5 ⇐
E+5 ⇐
S+5 ⇐
S+E ⇐
S
```

```
S → S + E | E
E → num | (S)
```

![](img/1db31d392048feae2d803578b3d5a4b9_289_0.png)

![](img/1db31d392048feae2d803578b3d5a4b9_289_1.png)

- **Parsing actions:** a sequence of **shift** and **reduce** operations.
- **Parser state:** a stack of terminals and non-terminals (grows to the right).
- **Current derivation step** = always stack + input.

| Derivation step | Step stack | Unconsumed input |
|---|---|---|
| `(1+2+(3+4))+5 ⇐` |  | `(1+2+(3+4))+5` |
|  | `(` | `1+2+(3+4))+5` |
|  | `(1` | `+2+(3+4))+5` |
| `(E+2+(3+4))+5 ⇐` | `(E` | `+2+(3+4))+5` |
| `(S+2+(3+4))+5 ⇐` | `(S` | `+2+(3+4))+5` |
|  | `(S+` | `2+(3+4))+5` |
|  | `(S+2` | `+(3+4))+5` |
| `(S+E+(3+4))+5 ⇐` | `(S+E` | `+(3+4))+5` |

![](img/1db31d392048feae2d803578b3d5a4b9_290_0.png)

![](img/1db31d392048feae2d803578b3d5a4b9_290_1.png)

1. **Shift**: Shift a terminal from the front of the input to the top of the stack.
2. **Reduce**: Reduce a string α at the top of the stack to a nonterminal A, given the BNF choice A → α.

**A bottom-up parser is a shift-reduce parser.**

One further feature of bottom-up parsers: grammars are always augmented with a **new start symbol**. If S is the start symbol, a new start symbol S′ is added to the grammar: S′ → S.

### Example 5.1

Consider the following augmented grammar for balanced parentheses:

```
S′ → S
S → (S)S | ε
```

Four steps of the rightmost derivation:

```
S′ ⇒ S ⇒ (S)S ⇒ (S) ⇒ ( )
```

|  | Parsing stack | Input | Action |
|---|---|---|---|
| 1 | `$` | `( ) $` | **Shift** |
| 2 | `$ (` | `) $` | **Reduce S → ε** |
| 3 | `$ (S` | `) $` | **Shift** |
| 4 | `$ (S )` | `$` | **Reduce S → ε** |
| 5 | `$ (S ) S` | `$` | **Reduce S → (S)S** |
| 6 | `$S` | `$` | **Reduce S′ → S** |
| 7 | `$S′` | `$` | **Accept** |

### Example 5.2

Consider the following augmented grammar for arithmetic expressions (no parentheses and one operation):

```
E′ → E
E → E + n | n
```

A bottom-up parse of the string `n + n`:

The rightmost derivation is `E′ ⇒ E ⇒ E + n ⇒ n + n`.

|  | Parsing stack | Input | Action |
|---|---|---|---|
| 1 | `$` | `n+n$` | **Shift** |
| 2 | `$n` | `+n$` | **Reduce E → n** |
| 3 | `$E` | `+n$` | **Shift** |
| 4 | `$E+` | `n$` | **Shift** |
| 5 | `$E+n` | `$` | **Reduce E → E+n** |
| 6 | `$E` | `$` | **Reduce E′ → E** |
| 7 | `$E′` | `$` | **Accept** |

### Right sentential form

- Each of the intermediate strings of terminals and nonterminals in such a derivation is called a right sentential form.
- Each such sentential form is split between the parsing stack and the input during a shift-reduce parse.

![](img/1db31d392048feae2d803578b3d5a4b9_294_0.png)

![](img/1db31d392048feae2d803578b3d5a4b9_294_1.png)

- Thus, E, E+, and E+n are all *viable prefixes* of the right sentential form E+n.
- The right sentential form n+n has ε and n as its viable prefixes.
- n+ is not a viable prefix of n+n.
- The sequence of symbols on the parsing stack is called *a viable prefix* of the right sentential form.
