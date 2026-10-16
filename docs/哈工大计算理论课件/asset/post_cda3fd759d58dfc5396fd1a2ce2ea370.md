
## Reductions via computation histories

- Construct a CFG $G$ for a TM $M$ and an input $w$. $G$ generates all strings if and only if $M$ does not accept $w$. This means that $G$ generates all strings that are not accepting computation histories for $M$ on $w$.

- An accepting computation history for $M$ on $w$ appears as $\#C_1\#C_2\#\cdots\#C_k$.

The strings that $G$ recognizes should be tested as follows:

- Test if the string starts with $C_1$. If it does not, *accept*; else
- Test if it ends with an accepting configuration $C_f$. If it does not, *accept*; else
- Test if every $C_i$ properly yields $C_{i+1}$ under the rules of $M$. If it does not, *accept*; else *reject*.

- Instead of actually constructing $G$, we construct a PDA $D$, then we certainly can convert $D$ to $G$.
- Since there are three conditions to test, we have to design $D$ with three copies.
  - One checks whether the beginning of the input string is $C_1$.
  - One checks whether the input string ends with a configuration containing the accept state, $q_{accept}$.
  - One checks whether every $C_i$ properly yields $C_{i+1}$ under the rules of $M$.

The third copy works as follows:

- Scan the input until it nondeterministically decides that it has come to $C_i$.
- Push $C_i$ onto the stack until it comes to the end marked by the $\#$ symbol.
- Pop the stack to compare with $C_{i+1}$. In the comparing process, the symbols popped from the stack are in the reverse order of $C_i$, so modify it by the following method:
- Method 1: in the beginning

  ```
  # ↔ # ↔ # ↔ # ↔ # ... # ↔ #
  C₁   C₂ᴿ   C₃   C₄ᴿ      Cₜ
  ```

- Method 2: in every step
  copy $C_i$ to another stack, then $C_i$ is in its order again.

- $D$ accepts if there is a mismatch or an improper update.

## Post correspondence problem

- The Post correspondence problem (PCP) is in fact an undecidable problem concerning simple manipulations of strings. Here we demonstrate it as a puzzle.
- There is a collection of dominos.

![](img/505b35cb28b35d38fc29ccba74c23087_368_0.png)

Not these dominos.

- Each domino contains two strings, one on each side.
- E.g., a collection of dominos looks like
- { [b / ca], [a / ab], [ca / a], [abc / c] }
- The task is to list a match, which is a list of these dominos (repetitions permitted), so that the string we get by reading off the symbols on the top is the same as the string of symbols on the bottom.

- A match for this puzzle:

  \[
  \frac{a}{ab}, \frac{b}{ca}, \frac{ca}{a}, \frac{a}{ab}, \frac{abc}{c}
  \]

- Or written as

![](img/505b35cb28b35d38fc29ccba74c23087_370_0.png)

For some collections of dominos, finding a match may not be possible. For example, the collection (every top string is longer than the corresponding bottom string)

\[
\left\{ \frac{ca}{a}, \frac{acc}{ba}, \frac{abc}{ab} \right\}
\]

Formally, PCP is a collection $P$ of dominos:

\[
P = \{ [t_1 / b_1], [t_2 / b_2], \ldots, [t_k / b_k] \}
\]

and a match is a sequence $i_1, i_2, \ldots, i_\ell$, where

\[
t_{i_1} t_{i_2} \cdots t_{i_\ell} = b_{i_1} b_{i_2} \cdots b_{i_\ell}.
\]

The problem is to determine whether $P$ has a match.

\[
PCP = \{ \langle P \rangle \mid P \text{ is an instance of the Post correspondence problem with a match} \}
\]

- Theorem: *PCP* is undecidable.

**Proof:**

- Assume that TM *R* decides *PCP*. Now use *R* to construct TM *S* to decide $A_{TM}$.
- Let $M = (Q, \Sigma, \Gamma, \delta, q_0, q_{accept}, q_{reject})$.
- Construct an instance of PCP $P$ that has a match iff $M$ accepts $w$.

- Construct an instance $P'$ of MPCP, where

\[
MPCP = \{ \langle P \rangle \mid P \text{ is an instance of the Post correspondence problem with a match that starts with the first domino} \}.
\]

- The following seven parts accomplish the simulation (explained in the example).
