
## Co-Turing-recognizable language

- \(\overline{A_{TM}}\) is not Turing-recognizable.
- **Proof:** \(A_{TM}\) is Turing-recognizable. If \(\overline{A_{TM}}\) also were Turing-recognizable, \(A_{TM}\) would be decidable. Since \(A_{TM}\) is not decidable, \(\overline{A_{TM}}\) must not be Turing-recognizable.

## Theory of Computation

### Lecture 7: Reducibility

Lecturer: Dr. Ng, Wing Yin

TA: Ms. Sun, Binbin

**MiLeS Computing Lab,**
Department of Computer Science and Technology,
Harbin Institute of Technology Shenzhen Graduate School.

## Content of Lecture 7

- Undecidable problems from language theory
  - Reduction
  - Computation history
- Post correspondence problem
- Mapping reducibility

## Reducibility

- We have used the proof-by-construction method to prove that some problems are decidable:
  \(A_{DFA}, A_{NFA}, A_{REX}, E_{DFA}, EQ_{DFA}\)
  \(A_{CFG}, E_{CFG}, \text{every CFL}\)
- The problem that we have proved to be undecidable is the halting problem \(A_{TM}\).

- In this chapter we first introduce a method called *reduction*, to prove that some problems are undecidable.
- A reduction is a way of converting one problem \(A\) to another problem \(B\) in such a way that a solution to problem \(B\) can be used to solve problem \(A\).
- When \(A\) is reducible to \(B\), solving \(A\) cannot be harder than solving \(B\), because a solution to \(B\) gives a solution to \(A\).

- **Example:**
  - Problem \(A\): measuring the area of a rectangle.
  - Problem \(B\): measuring the length and width of a rectangle.
  - We can **reduce** \(A\) to \(B\).

- **Example 2:**
  - Problem \(A\): solving a system of linear equations.
  - Problem \(B\): inverting a matrix.
  - We can **reduce** \(A\) to \(B\).

In decidability theory and complexity theory, reducibility is important.

If \(A\) is undecidable and reducible to \(B\), \(B\) is undecidable too. This is key to proving that various problems are undecidable, while we know that the halting problem \(A_{TM}\) is undecidable.

## Undecidable problems from language theory

- \(HALT_{TM} = \{\langle M, w\rangle \mid M \text{ is a TM and } M \text{ halts on input } w\}\)
  So \(HALT_{TM}\) determines whether a Turing machine halts on a given input.

- Prove \(HALT_{TM}\) is undecidable.
  **Proof:** This proof is by contradiction. Assume that \(HALT_{TM}\) is decidable. After showing that \(A_{TM}\) is reducible to \(HALT_{TM}\), we can conclude that \(A_{TM}\) is decidable, so there is a contradiction.

So from now on, we have a common strategy to prove a problem is undecidable, except for the undecidability of \(A_{TM}\) itself, which is proved directly via the diagonalization.

- \(E_{TM} = \{\langle M\rangle \mid M \text{ is a TM and } L(M)=\emptyset\}\)
- So \(E_{TM}\) determines whether a Turing-recognizable language is empty.
- Prove \(E_{TM}\) is undecidable.
  **Proof:** Ordinarily, \(A_{TM}\) means that for the encoding \(\langle M,w\rangle\), we cannot decide whether \(M\) recognizes \(w\). Assume that TM \(R\) decides \(E_{TM}\). Now use \(R\) to construct TM \(S\) to decide \(A_{TM}\). Instead of running \(R\) directly on \(\langle M\rangle\), we run \(R\) on a modification of \(\langle M\rangle\). Since we want to judge emptiness corresponding to recognizing \(w\), we modify \(\langle M\rangle\) to guarantee that the modified machine \(M_1\) rejects all strings except \(w\), and works as usual on input \(w\).

- The modified machine \(M_1\) works as follows:

  \(M_1 =\) “On input \(x\):
  1. If \(x \neq w\), *reject*.
  2. If \(x = w\), run \(M\) on \(w\) and *accept* if \(M\) does.”

- \(S =\) “On input \(\langle M,w\rangle\), an encoding of a TM \(M\) and a string \(w\):
  1. Run TM \(R\) on input \(\langle M_1\rangle\).
  2. If \(R\) accepts, *reject*; if \(R\) rejects, *accept*.”
