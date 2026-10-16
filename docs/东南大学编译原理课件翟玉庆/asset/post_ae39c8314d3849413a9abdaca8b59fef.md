
## CHAPTER 4 SYNTAX ANALYSIS

### Section 2 TOP-DOWN PARSING

#### 13、 Error recovery in predictive parsing

- Panic-mode error recovery
- Phrase-level recovery

### Section 3 BOTTOM-UP PARSING

#### 1、 Basic idea of bottom-up parsing

- Shift-reduce parsing
- Operator-precedence parsing
  - An easy-to-implement form
- LR parsing
  - A much more general method
  - Used in a number of automatic parser generators

#### 2、 Basic concepts in Shift-reducing Parsing

- Handles
- Handle Pruning

#### 3、 Stack implementation of Shift-Reduce parsing

![](img/353f619caa6c5715591f2105bdfa2865_251_0.png)

### Section 4 OPERATOR-PRECEDENCE PARSING

#### 1、The definition of an operator grammar

- The grammar has the property that no production right side is ε or has two adjacent non-terminals.
- E.g. `E→E+E|E−E|E*E|E/E|(E)|i`

#### 2、 Operator precedence relations

- Three disjoint precedence relations `<`, `≐`, `>` between certain pairs of terminals.

Between certain pairs of terminals a,b, which have the following forms: `...ab...`, `...aQb...`, and Q if non-terminal. Then the relationship of a and b is:

1. `a ≺ b` — a yields precedence to b
2. `a ≐ b` — a has the same precedence as b
3. `a ≻ b` — a takes precedence over b
4. For some terminals, we might have none of these relations.

Notes: These precedence relations can be used to guide the selection of handles.

| RS \ LS | + | * | ( | ) | i | $ |
|---|---|---|---|---|---|---|
| + | > | < | < | > | < | > |
| * | > | > | < | > | < | > |
| ( | < | < | < | = | < |  |
| ) | > | > |  | > |  | > |
| i | > | > |  | > |  | > |
| $ | < | < | < |  | < |  |

Related Grammar: `E→E+F|F`, `F→F*G|G`, `G→(E)|i`

#### 3、 Using Operator-Precedence Relations

Delimit the handle of a right sentential form, with `<` marking the left end, `=` appearing in the interior of the handle, and `>` marking the right end.

For the string `$i+i*i$`, how to find the handle:

1. Scan the string from the left end until the first `>` is encountered.
2. Then scan backwards over any `=`'s until a `<` is encountered.
3. The handle contains everything to the left of the first `>` and to the right of the `<` encountered in step 2, including any intervening or surrounding non-terminals.

#### 4、 Operator-precedence parsing Algorithm

- **Input.** An input string w and a table of precedence relations.
- **Output.** If w is well formed, a skeletal parse tree, with a placeholder non-terminal E labeling all interior nodes; otherwise, an error indication.
- **Method.** Initially, the stack contains `$` and the input buffer contains the string `w$`.

```
Set ip to point to the first symbol of w$;
while (1) {
    if ($ is on top of the stack and ip points to $) /*success*/
        return;
    else {
        let a be the topmost terminal symbol on the stack;
        let b be the symbol pointed to by ip;
        if (a⋖b || a≐b) /*Shift*/
        {
            push b onto the stack;
            advance ip to the next input symbol;
        }
    }
}
```

#### 5、 Construct the operator-precedence relationship table

- Construct the `FIRSTVT` and `LASTVT` for each non-terminal in the grammar.
- Find out the relations between each of the terminals.
