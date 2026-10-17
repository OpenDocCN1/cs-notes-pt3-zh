

## 3.4.3 The dangling else problem

- The dangling else problem has its origins in the syntax of Algol60.
- To design the syntax so that the dangling else problem does not appear.

- Require the presence of the else-part, and this method has been used in LISP and other functional languages (where a value must also be returned).
- Use a **bracketing keyword** for the if-statement; languages that use this solution include Algol68 and Ada.

- In Ada, for example, the programmer writes:

```ada
if x /= 0 then
   if y = 1/x then ok := true;
   else z := 1/x;
   end if;
end if;
```

- To associate the else-part with the second if-statement. Alternatively, the programmer writes:

```ada
if x /= 0 then
   if y = 1/x then ok := true;
   end if
else z := 1/x;
end if;
```

- BNF in Ada (somewhat simplified):

*if-stmt* → *if* *condition* **then** *statement-sequence* **end if**  
&nbsp;&nbsp;&nbsp;&nbsp;| *if* *condition* **then** *statement-sequence* **else**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*statement-sequence* **end if**

## 3.4.4 Inessential ambiguity

- Sometimes a grammar may be ambiguous and yet always produce unique abstract syntax trees.

The grammar ambiguously as:

```
stmt-sequence → stmt-sequence ; stmt-sequence
              | stmt
stmt → s
```

- Either a right recursive or left recursive grammar rule would still result in the same syntax tree structure.

- **Inessential ambiguity**: _the associated semantics do not depend on what disambiguating rule is used._

- Arithmetic addition or string concatenation.
- That represent **associative operations** (a binary operator · is associative if (a · b) · c = a · (b · c) for all values a, b, and c).

- The syntax trees are still distinct, semantic value are the same.

## 3.5 Extended notations: EBNF and syntax diagrams

- BNF notation is sometimes extended to include special notations for repetitive and optional constructs.

- Extended BNF, or EBNF.

Repetition:

A → A α | β (left recursive)

A → α A | β (right recursive)

EBNF opts to use curly brackets { . . } to express repetition.

A → β{α}

A → {α} β

- **Example:**

`stmt-Sequence → stmt ; stmt-Sequence | stmt`

`stmt → s`

- **In EBNF this would appear as**

`stmt-sequence → { stmt ; } stmt`

*(right recursive form)*

`stmt-sequence → stmt { ; stmt}`

*(left recursive form)*

- Optional constructs in EBNF are indicated by surrounding them with square brackets [...].

```
statement → if-stmt | other
if-stmt → if ( exp ) statement [ else statement ]
exp → 0 | 1
```

## 3.6 Formal properties of context-free language

**Definition**: A context-free grammar consists of the following:

1. A set T of **terminals**.
2. A set N of **nonterminals** (disjoint from T).
3. A set P of **productions**, or **grammar rules**, of the form A → a, where A is an element of N and a is an element of (T ∪ N)* (a possibly empty sequence of terminals and nonterminals).
4. A **start symbol** S from the set N.

