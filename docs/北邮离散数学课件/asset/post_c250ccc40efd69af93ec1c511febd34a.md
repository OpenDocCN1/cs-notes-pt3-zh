
## Disjunctive Normal Form

**Example**: Find the Disjunctive Normal Form (DNF) of

$$
(p \lor q) \to \neg r
$$

**Solution**: This proposition is true when $r$ is false or when both $p$ and $q$ are false.

$$
(\neg p \land \neg q) \lor \neg r
$$

## Conjunctive Normal Form

- A compound proposition is in *Conjunctive Normal Form* (CNF) if it is a conjunction of disjunctions.
- Every proposition can be put in an equivalent CNF.
- Conjunctive Normal Form (CNF) can be obtained by eliminating implications, moving negation inwards and using the distributive and associative laws.
- Important in resolution theorem proving used in artificial intelligence (AI).
- A compound proposition can be put in conjunctive normal form through repeated application of the logical equivalences covered earlier.

**Example**: Put the following into CNF:

$$
\neg(p \to q) \lor (r \to p)
$$

### Solution

1. Eliminate implication signs:

   $$
   \neg(\neg p \lor q) \lor (\neg r \lor p)
   $$

2. Move negation inwards; eliminate double negation:

   $$
   (p \land \neg q) \lor (\neg r \lor p)
   $$

3. Convert to CNF using associative/distributive laws:

   $$
   (p \lor \neg r \lor p) \land (\neg q \lor \neg r \lor p)
   $$

## Questions on Propositional Satisfiability

**Example**: Determine the satisfiability of the following compound propositions:

$$
(p \lor \neg q) \land (q \lor \neg r) \land (r \lor \neg p)
$$

**Solution**: Satisfiable. Assign **T** to $p$, $q$, and $r$.

$$
(p \lor q \lor r) \land (\neg p \lor \neg q \lor \neg r)
$$

**Solution**: Satisfiable. Assign **T** to $p$ and **F** to $q$.

$$
(p \lor \neg q) \land (q \lor \neg r) \land (r \lor \neg p) \land (p \lor q \lor r) \land (\neg p \lor \neg q \lor \neg r)
$$

**Solution**: Not satisfiable. Check each possible assignment of truth values to the propositional variables and none will make the proposition true.

## Notation

$\bigvee_{j=1}^{n} p_j$ is used for $p_1 \lor p_2 \lor \dots \lor p_n$.

$\bigwedge_{j=1}^{n} p_j$ is used for $p_1 \land p_2 \land \dots \land p_n$.

Needed for the next example.

## Sudoku

- A **Sudoku puzzle** is represented by a 9×9 grid made up of nine 3×3 subgrids, known as **blocks**. Some of the 81 cells of the puzzle are assigned one of the numbers 1, 2, ..., 9.
- The puzzle is solved by assigning numbers to each blank cell so that every row, column and block contains each of the nine possible numbers.
- Example

  ![](img/c25dfd82fc242c2db53bc942dcad6885_287_0.png)

## Encoding as a Satisfiability Problem

- Let $p(i,j,n)$ denote the proposition that is true when the number $n$ is in the cell in the $i$th row and the $j$th column.
- There are $9 \times 9 \times 9 = 729$ such propositions.
- In the sample puzzle $p(5,1,6)$ is true, but $p(5,j,6)$ is false for $j = 2, 3, \dots, 9$.

### Encoding (cont)

- For each cell with a given value, assert $p(i,j,n)$, when the cell in row $i$ and column $j$ has the given value.
- Assert that every row contains every number:

  $$
  \bigwedge_{i=1}^{9} \bigwedge_{n=1}^{9} \bigvee_{j=1}^{9} p(i,j,n)
  $$

- Assert that every column contains every number:

  $$
  \bigwedge_{j=1}^{9} \bigwedge_{n=1}^{9} \bigvee_{i=1}^{9} p(i,j,n)
  $$

- Assert that each of the 3×3 blocks contains every number:

  $$
  \bigwedge_{r=0}^{2} \bigwedge_{s=0}^{2} \bigwedge_{n=1}^{9} \bigwedge_{i=1}^{3} \bigwedge_{j=1}^{3} p(3r+i,3s+j,n)
  $$

  (This is tricky — ideas from Chapter 4 help.)

- Assert that no cell contains more than one number. Take the conjunction over all values of $n$, $n'$, $i$, and $j$, where each variable ranges from 1 to 9 and $n \neq n'$, of

  $$
  p(i,j,n) \to \neg p(i,j,n')
  $$

## Solving Satisfiability Problems

- To solve a Sudoku puzzle, we need to find an assignment of truth values to the 729 variables of the form $p(i,j,n)$ that makes the conjunction of the assertions true. Those variables that are assigned **T** yield a solution to the puzzle.
- A truth table can always be used to determine the satisfiability of a compound proposition. But this is too complex even for modern computers for large problems.
- There has been much work on developing efficient methods for solving satisfiability problems as many practical problems can be translated into satisfiability problems.
