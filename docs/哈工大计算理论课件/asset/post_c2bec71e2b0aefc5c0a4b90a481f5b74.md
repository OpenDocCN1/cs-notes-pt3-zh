
## Graph

- If every two nodes have a path between them, the graph is **connected**.
- A graph is a **tree** if it is connected and has no simple cycles.
  - Root, leaves.
- If the graph has arrows instead of lines, the graph is a directed graph.
  - Outdegree, indegree.
  - Directed path
  - Strongly connected

![](img/505b35cb28b35d38fc29ccba74c23087_31_0.png)

## String and languages

- **Alphabet** is a finite set that is nonempty.
  - Σ₁ = {0,1}
  - Γ₁ = {a,b,c,...,x,y,z}
- The members of the alphabet are the symbols.
- **String** is a finite sequence of symbols from that alphabet, usually written next to one another and not separated by commas.
  - w = w₁w₂...wₙ   |w| = n
  - **Reverse of w**: wᴿ = wₙ wₙ₋₁...w₁
  - **Empty string**: ε
  - String z is a substring of w if z appears consecutively within w.

- $x = x_1 x_2 \dots x_m$, $y = y_1 y_2 \dots y_n$
  - Concatenation of $x$ and $y$ is $xy = x_1 x_2 \dots x_m y_1 y_2 \dots y_n$
  - $x^k = \underbrace{xx\dots x}_{k}$

The lexicographic ordering of strings is the same as the dictionary ordering, except that shorter strings precede longer strings.

- lexicographic ordering over $\Sigma_1 = \{0,1\}$ is $\{\varepsilon,0,1,00,01,10,11,000,\dots\}$

- A language is a set of strings.

## Boolean logic

- Boolean logic is built around {TRUE, FALSE}.
- Boolean operation:
  - Negation (NOT)
    - ¬0=1, ¬1=0
  - Conjunction (AND)
    - 0∧0=0, 0∧1=0, 1∧0=0, 1∧1=1
  - Disjunction (OR)
    - 0∨0=0, 0∨1=1, 1∨0=1, 1∨1=1
  - Exclusive (XOR)
    - 0⊕0=0, 0⊕1=1, 1⊕0=1, 1⊕1=0,
  - Equality(↔)
    - 0↔0=1, 0↔1=0, 1↔0=0, 1↔1=1,
  - Implication(→)
    - 0→0=1, 0→1=1, 1→0=0, 1→1=1,

Equal relations:

- P ∨ Q      ¬(¬P ∧ ¬Q)
- P → Q      ¬P ∨ Q
- P ↔ Q      (P → Q) ∧ (Q → P)
- P ⊕ Q      ¬(P ↔ Q)
- P ∧ (Q ∨ R)      (P ∧ Q) ∨ (P ∧ R)
- P ∨ (Q ∧ R)      (P ∨ Q) ∧ (P ∨ R)

## Definitions, theorems and proofs

- Definition
- Theorem, lemma, corollary
- Proofs:
  - Proof by construction
  - Proof by contradiction
  - Proof by induction

- **Definitions** describe the objects and notions that we used
  - **Precision** is essential to any mathematical definition
  - **Mathematical Statement** state the property of a defined object
- **Proof** is a convincing logical argument that a statement is true
  - In mathematics, argument must be airtight and **convincing in absolute sense**
  - Evidence plays no role and we demand proof beyond any doubt

- **Theorem** is a mathematical statement proved true
- **Lemma** is a statement that we proved to assist in the proof of another more significant statement
- A theorem or its proof may allow us to conclude easily that another related statement is true and it is called **Corollary**
- The only way to determine the truth or falsity of a mathematical statement is with a mathematical proof.

## Proof by construction

- **proof by construction**
  - Many theorem state that a particular type of object exists.
  - One way to prove the theorems that state a particular type of object exists is by demonstrating how to construct the object

- Example 1: Prove for each even number $n$ greater than 2, there exists a 3-regular graph (a graph with degree 3 for all of its nodes) with $n$ nodes.
- Proof: Let $n$ be an even number and $n > 2$. Construct graph $G = (V, E)$ with n nodes as follows. The set of nodes of $G$ is $V = \{0,1,\dots,n-1\}$, and the set of edges of $G$ is the set $E = \{\{i,i+1\} \mid for\ 0 \le i \le n-2\} \cup \{\{n-1,0\}\} \cup \{\{i,i+n/2\} \mid for\ 0 \le i \le n/2-1\}$
