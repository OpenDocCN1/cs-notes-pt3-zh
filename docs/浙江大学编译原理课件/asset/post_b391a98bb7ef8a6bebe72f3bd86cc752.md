

## 3.4.1 Ambiguity grammars

To remove the given ambiguity in our simple expression grammar:

- state a disambiguating rule that establishes the relative precedences of the three operations represented.
- the associativity of each of the operations of addition, subtraction, and multiplication.

specify that an operation is nonassociative, in that a sequence of more than one operator in an expression is not allowed.

```
exp → factor op factor | factor
factor → ( exp ) | number
op → + | - | *
```

## 3.4.2 Precedence and associativity

- group the operators into groups of equal precedence, and for each precedence we must write a different rule.
- For example, the precedence of multiplication over addition and subtraction can be added to our simple expression grammar as follows:

```
exp    → exp addop exp | term
addop  → + | -
term   → term mulop term | factor
mulop  → *
factor → ( exp ) | number
```

- **addition** and **subtraction** will appear "higher" (that is, closer to the root) in the parse and syntax trees, and thus receive lower precedence.
- a precedence cascade: a grouping of operators into different precedence levels is a standard method in syntactic specification using **BNF**.

- a left recursive rule makes its operators associate on the left
- a right recursive rule makes them associate on the right.

*exp* → *exp addop exp* | *term*

replacing the rule by

*exp* → *exp addop term* | *term*    (left associative)

*exp* → *term addop exp* | *term*    (right associative)

- complete the removal of ambiguity in the BNF rules for our simple arithmetic expressions:

```
exp → exp addop term | term
addop → + | -
term → term mulop factor | factor
mulop → *
factor → ( exp ) | number
```

the parse tree for the expression 34-3*42

the parse tree for the expression 34-3-42

the precedence cascades cause the parse trees to become much more complex. The syntax trees, however, are not affected.

## 3.4.3 The dangling else problem

- Which one is correct depends on whether we want to associate the single else-part with the first or the second if-statement:

the first parse tree associates the else-part with the first if-statement;
the second parse tree associates it with the second if-statement.

- This ambiguity is called the **dangling else problem**.

an else-part should always be associated with
the nearest if-statement that does not yet have
an associated else-part.

- This disambiguating rule is called the **most closely nested rule** for the dangling else problem.
- if we wanted we could associate the else-part with the first if-statement by using brackets {…} in C, as in
if (x != 0)
{ if (y == 1/x) ok = TRUE; }
else z = 1/x;

