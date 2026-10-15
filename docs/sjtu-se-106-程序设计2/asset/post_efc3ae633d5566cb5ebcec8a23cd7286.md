
## Parsing Strategies

## Zhengwei QI

Most slides from Eric Roberts, CS 106B, Stanford

## Updated Slide on Job Outlook

![](img/af430dff16b82a0fe61ce7dee05dcf9c_452_0.png)

> We are very happy with the students that we get from this university. . . . We just wish we could hire two to three times as many of them.
> — Bill Gates at Stanford, February 19, 2008

## Outline for Today

- 1. Review the expression hierarchy
- 2. Walk through a simple evaluation
- 3. Explore the relationship between parsing and grammars
- 4. Look at the final version of `parser.cpp`
- 5. Walk through an example of the parser in action
- 6. Review the structure of the Basic assignment

## The Expression Hierarchy

- On last course, I defined an abstract `Expression` class with three concrete subclasses, one for each of the expression types:

![](img/af430dff16b82a0fe61ce7dee05dcf9c_455_0.png)

## Code for the eval Method

```
int ConstantExp::eval(EvalState & state) {
    return value;
}

int IdentifierExp::eval(EvalState & state) {
    if (!state.isDefined(name)) error(name + " is undefined");
    return state.getValue(name);
}

int CompoundExp::eval(EvalState & state) {
    if (op == "=") {
        if (lhs->getType() != IDENTIFIER) error("Illegal lhs in assignment");
        int val = rhs->eval(state);
        state.setValue(((IdentifierExp *) lhs)->getName(), val);
        return val;
    }
    int left = lhs->eval(state);
    int right = rhs->eval(state);
    if (op == "+") return left + right;
    if (op == "-") return left - right;
    if (op == "*") return left * right;
    if (op == "/") return left / right;
    if (op == "%") return left % right;
    error("Illegal operator in expression");
    return 0;
}
```

## Exercise: Evaluating an Expression

- Assuming **x** is bound to 3, trace through the steps in evaluating

y = ( 9 - x ) * 7

![](img/af430dff16b82a0fe61ce7dee05dcf9c_457_0.png)

## The Problem of Parsing

- On last course, I noted that the rules for forming an expression can be expressed in the form of a **grammar**, as follows:

E → constant
E → identifier
E → E op E
E → ( E )

- The process of translating an expression from a string to its internal form is called **parsing**.

## A Two-Level Grammar

- The problem of parsing an expression can be simplified by changing the grammar to one that has two levels:
  - An *expression* is either a *term* or two expressions joined by an operator.
  - A *term* is either a constant, an identifier, or an expression enclosed in parentheses.

- This design is reflected in the following revised grammar.

```
E → T
E → E op E

T → constant
T → identifier
T → ( E )
```

## Ambiguity in Parse Structures

- Although the two-level grammar from the preceding slide can recognize any expression, it is *ambiguous* because the same input string can generate more than one parse tree.

![](img/af430dff16b82a0fe61ce7dee05dcf9c_460_0.png)

![](img/af430dff16b82a0fe61ce7dee05dcf9c_460_1.png)

- Ambiguity in grammars is typically resolved by providing the parser with information about the *precedence* of the operators. The text describes two strategies: *Iversonian precedence*, in which the operators all group to the right, and *operator precedence*, in which each operator is associated with an integer that defines its place in the precedence hierarchy.

## Exercise: Parsing an Expression

- Diagram the expression tree that results from the input string

odd = 2 * n + 1

![](img/af430dff16b82a0fe61ce7dee05dcf9c_461_0.png)

## The parser.cpp Implementation

```
/*
 * Implementation notes: readE
 * Usage: exp = readE(scanner, prec);
 * --------------------------------
 * This function reads the next expression from the scanner by
 * matching the input to the following ambiguous grammar:
 *
 *     E -> T
 *     E -> E op E
 *
 * This version of the method uses precedence to resolve ambiguity.
 */

Expression *readE(TokenScanner & scanner, int prec) {
    Expression *exp = readT(scanner);
    string token;
    while (true) {
        token = scanner.nextToken();
        int newPrec = precedence(token);
        if (newPrec <= prec) break;
        Expression *rhs = readE(scanner, newPrec);
        exp = new CompoundExp(token, exp, rhs);
    }
    scanner.saveToken(token);
    return exp;
}
```
