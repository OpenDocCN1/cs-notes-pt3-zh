
## Complexity relationship among models

- Let M be a k-tape TM that runs in $t(n)$ time. We construct a single tape TM S that runs in $O(t^2(n))$ time.
- Copy content of $M$'s $k$ tapes on $S$ consecutively, with the positions of $M$'s heads marked on the appropriate squares. This will take $O(n)$ time.

- To simulate each step of M

  I. S scans all the information stored on its tape to determine the symbols under M's tape head

  II. then S makes another pass over its tape to update the tape contents and head position.

Note: if one of M's heads moves rightward onto the previously unread portion of its tape, S must increase the amount of space allocated to this tape. We have to shift a portion of its own tape one cell to the right.

- To finish II, the length of the active portion of S’s tape determines how long S takes to scan it. We take the sum of the lengths of the active portions of M’s k tapes as an upper bound.

M uses t(n) tape cells in t(n) steps if the head moves rightward at every step and fewer if a head ever moves leftward, so each of these active portions has length at most t(n). So a scan of the active portion of S’s tape uses O(t(n))

- For each of M’s step, uses O(t(n)) time for one tape’s shift. So the total k shifts uses O(t(n)) time.
- There are t(n) steps of M, so this part of the simulation uses t(n) × O(t(n)) = O(t²(n)) time.
- Together with the initial stage the simulation uses O(t(n)) + O(t²(n))^{t(n) ≥ n} = O(t²(n)) time.

- Definition of the running time of a nondeterministic Turing machine:
  - Let $N$ be a nondeterministic Turing machine that is a decider. The running time of $N$ is the function $f : N \to N$, where $f(n)$ is the maximum number of steps that $N$ uses on any branch of its computation on any input of length $n$.

Time complexity of deterministic TM and nondeterministic TM:

![](img/505b35cb28b35d38fc29ccba74c23087_509_0.png)

Theorem:

- Let $t(n)$ be a function, where $t(n) \ge n$. Then every $t(n)$ time nondeterministic single-tape Turing machine has an equivalent $2^{O(t(n))}$ time deterministic single-tape Turing machine.

- Proof idea: the same as we have used to convert any nondeterministic single-tape TM into a deterministic single-tape TM to simulates it.

- Proof:
- Let $N$ be a nondeterministic TM running in $t(n)$ time. Construct a deterministic TM $D$ that simulates $N$ by searching $N$'s nondeterministic computation tree.
- Every branch of $N$'s nondeterministic computation tree has a length of at most $t(n)$. Let $b$ be the maximum number of legal choice given by $N$'s transition function. So every node in the tree can have at most $b$ children, and the total number of leaves in the tree is at most $b^{t(n)}$.

- By the property of tree, the total number of nodes in the tree is less than twice the maximum number of leaves, so the number of nodes are bounded by $O(b^{t(n)})$. Each travel from root to node is $O(t(n))$. Therefore the running time of D is $O(t(n)b^{t(n)}) = 2^{O(t(n))}$.

- Recall TM $D$ is a three-tape TM, by the last theory the running time of the deterministic single-tape TM is $\left(2^{O(t(n))}\right)^2 = 2^{O(2t(n))} = 2^{O(t(n))}$.

![](img/505b35cb28b35d38fc29ccba74c23087_513_0.png)

## Notice

- There is at most a square or polynomial difference (which is believed to be the minimal) between the time complexity of problems measured on deterministic single-tape and multitape TM.

- But there is an exponential difference (which is believed to be the maximal) between the time complexity of problems on deterministic and nondeterministic TM.

- This introduces the P and NP class problem.
