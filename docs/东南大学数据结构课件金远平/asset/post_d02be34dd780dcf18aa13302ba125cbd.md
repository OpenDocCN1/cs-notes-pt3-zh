
A B / C − D E \* + A C \* −

| operation | postfix |
|---|---|
| T₁ = A / B | T₁ C − D E \* + A C \* − |
| T₂ = T₁ − C | T₂ D E \* + A C \* − |
| T₃ = D \* E | T₂ T₃ + A C \* − |
| T₄ = T₂ + T₃ | T₄ A C \* − |
| T₅ = A \* C | T₄ T₅ − |
| T₆ = T₄ − T₅ | T₆ |

T₆ is the result.

### Virtues of postfix:

- No need for parentheses.
- The priority of the operators is no longer relevant.

These make the evaluation of postfix easy: make a left-to-right scan, stack operands, and evaluate operators using the correct number of operands from the stack, and place the result onto the stack.

```text
void Eval(Expression e)
{
    // evaluate the postfix expression e. It is assumed that the
    // last token in e is '#'. A function NextToken is used to get
    // the next token from e. Use stack.
    Stack<Token> stack;  //initialize stack
    for (Token x = NextToken(e); x != '#'; x = NextToken(e))
        if (x is an operand) stack.Push(x);
        else {  // operator
            remove the correct number of operands for operator x
            from stack; perform the operation x and store the result
            (if any) onto the stack;
        }
}
```

### 3.6.3 Infix to Postfix

Idea: note that the order of the operands in both infix and postfix is the same; we can form the postfix by immediately passing any operands to the output, then store the operators in a stack until just the right time.

e.g.

A\*(B+C)\*D → ABC+\*D\*

The algorithm behaves as:

| Next token | stack | output |
|---|---|---|
| A | empty | A |
| \* | empty | A |
| ( | \*( | A |
| B | \*( | AB |
| + | \*(+ | AB |
| C | \*(+ | ABC |
| ) | \* | ABC+ |
| \* | \* | ABC+\* |
| D | \* | ABC+\*D |
| done | empty | ABC+\*D\* |

![](img/15e8d7d94d8ddf02cb6839870195a31e_169_0.png)

From the example, we can see the left parenthesis behaves as an operator with high priority when it is not in the stack, whereas once it gets in, it behaves as one with low priority.

- isp (in-stack priority)
- icp (in-coming priority)
- The isp and icp of all operators in Fig. 3.15 remain unchanged.
- isp('(') = 8, icp('(') = 0, isp('#') = 8

**Hence the rule:**

Operators are taken out of stack as long as their isp is numerically less than or equal to the icp of the new operator.

```text
void Postfix(Expression e)
{ // output the postfix of the infix expression e. It is assumed
  // that the last token in e is '#'. Also, '#' is used at the bottom
  // of the stack.
  Stack<Token> stack; //initialize stack
  stack.Push('#');

  for (Token x = NextToken(e); x != '#'; x = NextToken(e))
      if (x is an operand) cout << x;
      else if (x == ')')
      { // unstack until '('
          for (; stack.Top() != '('; stack.Pop())
              cout << stack.Top();
          stack.Pop(); // unstack '('
      }
      else { // x is an operator
          for (; isp(stack.Top()) <= icp(x); stack.Pop())
              cout << stack.Top();
          stack.Push(x);
      }
  // end of expression, empty the stack
  for (; !stack.IsEmpty(); cout << stack.Top(), stack.Pop());
  cout << endl;
}
```

## Chapter 4 Linked Lists

### 4.1 Singly Linked Lists or Chains

The representation of a simple data structure using an array and a sequential mapping has the property:

Successive nodes of the data object are stored at fixed distance apart.

This makes it easy to access an arbitrary node in O(1).

### Disadvantage of sequential mapping:

Insertion and deletion are expensive, e.g.:

Insert "GAT" into or delete "LAT" from

(BAT, CAT, EAT, FAT, HAT, JAT, LAT, MAT, OAT, PAT, RAT, SAT, TAT, VAT, WAT)

— need data movement.

### Solution — linked representation:

- Items of a list may be placed anywhere in the memory.
- Associated with each item is a pointer (link) to the next item.

![](img/15e8d7d94d8ddf02cb6839870195a31e_177_0.png)

In a linked list, insertion (deletion) of arbitrary elements is much easier:

The above structures are called singly linked lists or chains, in which each node has exactly one pointer field.
