
## 4.3.3 Constructing LL(1) Parsing Tables

- **Example:** The simplified grammar of if-statements

**statement** → **if-stmt** | **other**

**if-stmt** → **if (exp) statement else-part**

**else-part** → **else statement** | ε

**exp** → 0 | 1

**The First sets:**

First(statement) = {if, other}
First(if-stmt) = {if}
First(else-part) = {else, ε}
First(exp) = {0, 1}

**The Follow sets:**

Follow(statement) = {$, else}
Follow(if-stmt) = {$, else}
Follow(else-part) = {$, else}
Follow(exp) = {)}

| M[N,T] | if | other | else | 0 | 1 | $ |
|---|---|---|---|---|---|---|
| statement | statement → if-stmt | statement → other |  |  |  |  |
| if-stmt | if-stmt → if (exp) statement else-part |  |  |  |  |  |
| else-part |  |  | else-part → else statement<br>else-part → ε |  |  | else-part → ε |
| exp |  |  |  | exp → 0 | exp → 1 |  |

- **Example:** Consider the following grammar with left factoring applied.

1. `stmt-sequence → stmt stmt-seq’`
2. `stmt-seq’ → ; stmt-sequence | ε`
3. `stmt → s`

**The First sets:**

First(stmt-sequence) = {s}
First(stmt) = {s}
First(stmt-seq’) = {;, ε}

**The Follow sets:**

Follow(stmt-sequence) = {$}
Follow(stmt) = {;, $}
Follow(stmt-seq’) = {$}

| M[N,T] | s | ; | $ |
|---|---|---|---|
| stmt-sequence | stmt-sequence → stmt stmt-seq’ |  |  |
| stmt | stmt → s |  |  |
| stmt-seq’ |  | stmt-seq’ → ; stmt-sequence | stmt-seq’ → ε |

![](img/1db31d392048feae2d803578b3d5a4b9_269_0.png)

## 4.5 Error Recovery in Top-Down Parsers

- **Different levels of response to errors.**

1. Give a meaningful error message; determine as closely as possible the location where that error has occurred.
2. Some form of error correction; (error repair) the parser attempts to infer a correct program from the incorrect one given.

- **Most of the techniques for error recovery are ad hoc, and general principles are hard to come by.**

![](img/1db31d392048feae2d803578b3d5a4b9_270_0.png)

### Some important considerations that apply are the following:

1. To determine that an error has occurred as soon as possible.
2. After an error has occurred pick a likely place to resume the parse, try to parse as much of the code as possible.
3. To avoid the error cascade problem.
4. To avoid infinite loops on error.

- The basic mechanism of panic mode:
  - A set of **synchronizing tokens** are provided to each recursive procedure;
  - If an error is encountered, the parser scans ahead, throwing away tokens until one of the synchronized tokens is seen in the input, and then parsing is resumed.

- **Check-input procedure: performs the early look-ahead checking**

```text
Procedure Checkinput(Firstset, Followset)
Begin
    If not (token in Firstset) then
        Error;
        Scanto(Firstset ∪ Followset)
    End if;
End;
```

- **Scanto procedure:**

```text
Procedure Scanto(synchset)
Begin
    While not (token in synchset ∪ {$}) do
        gettoken;
End Scanto;
```

- **Procedure exp(synchset):**

```text
Procedure exp(synchset)
Begin
    Checkinput({(, number}, synchset);
    If not (token in synchset) then
        term(synchset);
        While token = + or token = - do
            match(token);
            term(synchset);
        End while;
    Checkinput(synchset, {(, number});
    End if;
End exp;
```

![](img/1db31d392048feae2d803578b3d5a4b9_276_0.png)

![](img/1db31d392048feae2d803578b3d5a4b9_276_1.png)

- **Procedure factor(synchset):**

```text
Procedure factor(synchset)
Begin
    Checkinput({(, number}, synchset);
    If not (token in synchset) then
        case token of
            (: match(();
               exp({ });
               match());
            number:
               match(number);
            else error;
        end case;
    Checkinput(synchset, {(, number});
    End if;
End factor;
```

![](img/1db31d392048feae2d803578b3d5a4b9_277_0.png)

![](img/1db31d392048feae2d803578b3d5a4b9_277_1.png)
