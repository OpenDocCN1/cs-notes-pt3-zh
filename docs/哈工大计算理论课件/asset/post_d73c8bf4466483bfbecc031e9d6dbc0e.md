
## Regular expressions

### On class exercise

- Convert the DFAs into regular expressions.

![](img/505b35cb28b35d38fc29ccba74c23087_140_0.png)

![](img/505b35cb28b35d38fc29ccba74c23087_141_0.png)

## Nonregular languages

- Finite automata have finite states, so there are some languages that FA can't recognize.
  - E.g., $B = \{0^n1^n \mid n \geq 0\}$
- To prove a language is nonregular, we state a property that a regular language possesses.
- The pumping lemma for regular languages:
  - All strings in a regular language can be "pumped" if they are at least as long as a certain special value, called the pumping length.
- This lemma means that such a string contains a section that can be repeated any number of times with the resulting string remaining in the language.

### Pumping lemma

If $A$ is a regular language, then there is a number $p$ (the pumping length) where, if $s$ is any string in $A$ of length at least $p$, then $s$ may be divided into three pieces, $s = xyz$, satisfying the following conditions:

- For each $i \geq 0$, $xy^iz \in A$
- $|y| > 0$, and
- $|xy| \leq p$

- Note: The complete proof is provided on p. 79-80 in the English version, p. 48 in the Chinese version, and we only provide the idea of the proof in these lecture notes.

- Let $M = (Q, \Sigma, \delta, q_1, F)$ be a DFA that recognizes $A$.
- Assign the pumping length $p$ to be the number of states of $M$.
- We now prove that a string $s$ (with $|s| = n$ and $|s| \geq p$) belonging to $A$ can be divided into 3 pieces $xyz$ satisfying the three conditions.
- Suppose the state sequence is $q_1, q_{k_1}, \ldots, q_{k_n}$, where $q_{k_n} \in F$, so there are $n+1$ states, and since $n \geq p$, we have $n+1 > p$. By the pigeonhole principle, the sequence must contain a repeated state.
- Suppose state $q_9$ is the state that repeats first.

![](img/505b35cb28b35d38fc29ccba74c23087_145_0.png)

- Let $x = [q_1, q_9]$, $y = [q_{10}, q_9]$, $z = [q_9, q_{13}]$.

![](img/505b35cb28b35d38fc29ccba74c23087_146_0.png)

- By condition 1, we can see that $M$ accepts $xyyz$, and so does $xy^iz$.
- Obviously $|y| > 0$.
- As state $q_9$ is the state that repeats first, by the pigeonhole principle, the first $p+1$ states in the sequence must contain a repetition. So $|xy| \leq p$.

- Using the pumping lemma to prove a language $B$ is not regular:
  - Assume $B$ is regular to prove by contradiction.
  - Use the pumping lemma to guarantee the existence of a pumping length $p$ such that all strings of length $p$ or greater in $B$ can be pumped.
  - Find a string $s$ in $B$ that has length $p$ or greater but that cannot be pumped.
  - Demonstrate that $s$ cannot be pumped by considering all ways of dividing $s$ into $x$, $y$, and $z$ and, for each such division, finding a value $i$ where $xy^iz \notin B$. Therefore, there is a contradiction.

### Example

- $B = \{0^n1^n \mid n \geq 0\}$ is not regular.
- Proof:
- Assume that $B$ is regular.
- Let $p$ be the pumping length given by the pumping lemma.
- Choose $s$ to be the string $0^p1^p$. Because $s$ is a member of $B$ and $s$ has length more than $p$, the pumping lemma guarantees that $s$ can be split into three pieces, $s = xyz$, where for any $i \geq 0$ the string $xy^iz$ is in $B$.
- $y$ consists only of **0**s. In this case the string $xyyz$ has more **0**s than **1**s and so is not a member of $B$, violating condition 1.
- $y$ consists only of **1**s. In this case the string $xyyz$ has more **1**s than **0**s and so is not a member of $B$, violating condition 1.
- $y$ consists of both **0**s and **1**s. $xyyz$ may have the same number of **0**s and **1**s, but there must be a **1** before **0**, and so is not a member of $B$.
- Thus a contradiction is unavoidable, and $B$ is not regular.

### On class exercise

- Prove that $B_1 = \{0^n 1^n 2^n \mid n \geq 0\}$ is not regular.
