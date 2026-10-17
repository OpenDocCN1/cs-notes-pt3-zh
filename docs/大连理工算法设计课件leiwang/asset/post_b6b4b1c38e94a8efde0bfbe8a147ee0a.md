
## Solving the recurrence

\[
T(n) = T\left(\frac{1}{5}n\right) + T\left(\frac{3}{4}n\right) + \Theta(n)
\]

### Substitution

\[
T(n) \le cn
\]

\[
T(n) \le \frac{1}{5}cn + \frac{3}{4}cn + \Theta(n)
\]

\[
= \frac{19}{20}cn + \Theta(n)
\]

\[
= cn - \left(\frac{1}{20}cn - \Theta(n)\right)
\]

\[
\le cn,
\]

if \(c\) is chosen large enough to handle both the \(\Theta(n)\) and the initial conditions.

## Conclusions

- Since the work at each level of recursion is a constant fraction (19/20) smaller, the work per level is a geometric series dominated by the linear work at the root.
- In practice, this algorithm runs slowly, because the constant in front of \(n\) is large.
- The randomized algorithm is far more practical.

### Exercise: Why not divide into groups of 3?

## Introduction to Algorithms

6.046J/18.401J

![](img/5e59105b951890406cf98b2a964cb2f9_406_0.png)

**LECTURE 7**

## Hashing I

- Direct-access tables
- Resolving collisions by chaining
- Choosing hash functions
- Open addressing

Prof. Charles E. Leiserson

### Symbol-table problem

Symbol table \(S\) holding \(n\) **records**:

![](img/5e59105b951890406cf98b2a964cb2f9_407_0.png)

**Operations on \(S\):**

- \(\text{INSERT}(S, x)\)
- \(\text{DELETE}(S, x)\)
- \(\text{SEARCH}(S, k)\)

How should the data structure \(S\) be organized?

### Direct-access table

**IDEA:** Suppose that the keys are drawn from the set \(U \subseteq \{0, 1, \dots, m-1\}\), and keys are distinct. Set up an array \(T[0 \dots m-1]\):

\[
T[k] =
\begin{cases}
x & \text{if } x \in K \text{ and } key[x] = k, \\
\text{NIL} & \text{otherwise.}
\end{cases}
\]

Then, operations take \(\Theta(1)\) time.

**Problem:** The range of keys can be large:

- 64-bit numbers (which represent 18,446,744,073,709,551,616 different keys),
- character strings (even larger!).

### Hash functions

**Solution:** Use a _hash function_ \(h\) to map the universe \(U\) of all keys into \(\{0, 1, \dots, m-1\}\):

![](img/5e59105b951890406cf98b2a964cb2f9_409_0.png)

When a record to be inserted maps to an already occupied slot in \(T\), a _collision_ occurs.

### Resolving collisions by chaining

- Link records in the same slot into a list.

![](img/5e59105b951890406cf98b2a964cb2f9_410_0.png)

\[
h(49) = h(86) = h(52) = i
\]

### Worst case

- Every key hashes to the same slot.
- Access time = \(\Theta(n)\) if \(|S| = n\)

### Average-case analysis of chaining

We make the assumption of **simple uniform hashing**:

- Each key \(k \in S\) is equally likely to be hashed to any slot of table \(T\), independent of where other keys are hashed.

Let \(n\) be the number of keys in the table, and let \(m\) be the number of slots.

Define the **load factor** of \(T\) to be

\[
\alpha = n/m = \text{average number of keys per slot}.
\]

### Search cost

The expected time for an **unsuccessful** search for a record with a given key is

\[
\Theta(1 + \alpha).
\]

- apply hash function and access slot
- search the list

Expected search time \(= \Theta(1)\) if \(\alpha = O(1)\), or equivalently, if \(n = O(m)\).

A **successful** search has the same asymptotic bound, but a rigorous argument is a little more complicated. (See textbook.)

### Choosing a hash function

The assumption of simple uniform hashing is hard to guarantee, but several common techniques tend to work well in practice as long as their deficiencies can be avoided.

### Desiderata

- A good hash function should distribute the keys uniformly into the slots of the table.
- Regularity in the key distribution should not affect this uniformity.
