
## Relativization

### Definition:
- An oracle for a language A is device that is capable of reporting whether any string w is a member of A.
- An oracle Turing machine M^A is a modified TM that has the additional capability of querying an oracle.
- Whenever M^A writes a string on a special oracle tape it is informed whether that string is a member of A, in a single computation step
- Let P^A be the class of language decidable with a polynomial time oracle TM that uses oracle A.
- Define NP^A similarly

## Relativization

- Just as P^{SAT} contains language that we believe are not in P, the class NP^{SAT} contains languages that we believe are not in NP!
- Let say we have two Boolean formulas φ and ψ over variables x₁,...,xₗ are equivalent if the formulas have the same value on any assignment to the variables
  - A formula is minimal if no smaller formula is equivalent to it
  - NONMIN-FORMULA
    = { < φ > | φ is not a minimal Boolean formula }

## Relativization

- NONMIN-FORMULA does not seem to be in NP
- However, NONMIN-FORMULA is in NP^{SAT} because a nondeterministic polynomial time oracle TM with a SAT oracle can test whether φ is a member
  - First, inequivalence problem for two Boolean formulas is solvable in NP, hence the equivalence problem is in coNP
    - A nondeterministic TM can guess the assignment on which the two formulas have different values
  - Then the nondeterministic oracle TM for NONMIN-FORMULA nondeterministically guesses the smaller equivalent formula
    - Test whether it actually is equivalent using the SAT oracle and accept it

## Relativization

- Limits of the diagonalization method
  - We demonstrate A and B for which P^A and NP^A are provably different and P^B and NP^B are provably equal.
  - This is important because their existence indicates that we are unlikely to resolve the P versus NP question by using the diagonalization method.
  - The core of diagonalization method is a simulation of one TM by another.
  - The simulation is done so that the simulating machine can determine the behavior of the other machine and then behave differently

## Relativization

- Limits of the diagonalization method
  - Hence, diagonalization is not sufficient to separate these two classes
  - Similarly, no proof that relies on a simple simulation could show that the two classes are the same because that would show that they are the same relative to any oracle, but in fact P^A and NP^A are different.

## Relativization

- Theorem
  - An oracle $A$ exists whereby P$^A$ ≠ NP$^A$
  - An oracle $B$ exists whereby P$^B$ = NP$^B$

## Relativization

- Proof Idea:
  - Exhibiting oracle B is easy.
  - Let B be any PSPACE-complete problem such as TQBF
  - We exhibit oracle A by construction. We design A so that a certain language L_A in NP^A provably requires brute-force search. So, L_A can not be in P^A
  - Hence, we can conclude that P^A is not equal to NP^A
  - The construction considers every polynomial time oracle machine in turn and ensures that each fails to decide the language L_A

## Relativization

- In summary
  - The relativization method tells us that to solve the P versus NP question, we must analyze computations, not just simulate them
  - Circuit Complexity is one of the approaches

## Circuit Complexity

- Computers are built from electronic devices wired together in a design called a **digital circuit**
- We simulate TM with its theoretical counterpart to digital circuit, called **Boolean circuits**
- Researchers believe that circuits provide a convenient computational model for attacking P vs NP and related questions
- Circuits provide an alternative proof of the Cook-Levin theorem that SAT is NP-complete
