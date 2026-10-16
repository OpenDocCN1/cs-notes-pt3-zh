
## Big Theta Notation

**Example:** Show that the sum of the first *n* positive integers is Θ(*n*²).

**Solution:** Let *f(n)* = 1 + 2 + ··· + *n*.

- We have already shown that *f(n)* is O(*n*²).
- To show that *f(n)* is Ω(*n*²), we need a positive constant *C* such that *f(n)* > *Cn*² for sufficiently large *n*. Summing only the terms greater than *n*/2 we obtain the inequality

  1 + 2 + ··· + *n* ≥ ⌈*n*/2⌉ + (⌊*n*/2⌋ + 1) + ··· + *n*

  ≥ ⌈*n*/2⌉ + ⌈*n*/2⌉ + ··· + ⌈*n*/2⌉

  = (*n* − ⌈*n*/2⌉ + 1)⌈*n*/2⌉

  ≥ (*n*/2)(*n*/2) = *n*²/4
- Taking *C* = ¼, *f(n)* > *Cn*² for all positive integers *n*. Hence, *f(n)* is Ω(*n*²), and we can conclude that *f(n)* is Θ(*n*²).

## Big-Theta Notation

**Example**: Show that $f(x) = 3x^2 + 8x \log x$ is $\Theta(x^2)$.

**Solution:**

- $3x^2 + 8x \log x \le 11x^2$ for $x > 1$, since $0 \le 8x \log x \le 8x^2$.
- Hence, $3x^2 + 8x \log x$ is $O(x^2)$.
- $x^2$ is clearly $O(3x^2 + 8x \log x)$
- Hence, $3x^2 + 8x \log x$ is $\Theta(x^2)$.

## Big-Theta Notation

- When $f(x)$ is $\Theta(g(x))$ it must also be the case that $g(x)$ is $\Theta(f(x))$.
- Note that $f(x)$ is $\Theta(g(x))$ if and only if it is the case that $f(x)$ is $O(g(x))$ and $g(x)$ is $O(f(x))$.
- Sometimes writers are careless and write as if big-O notation has the same meaning as big-Theta.

## Big-Theta Estimates for Polynomials

**Theorem:** Let \(f(x)=a_nx^n+a_{n-1}x^{n-1}+\cdots+a_1x+a_0\), where \(a_0,a_1,\ldots,a_n\) are real numbers with \(a_n\ne0\). Then \(f(x)\) is of order \(x^n\) (or \(\Theta(x^n)\)). (The proof is an exercise.)

**Example:**

The polynomial \(f(x)=8x^5+5x^2+10\) is order of \(x^5\) (or \(\Theta(x^5)\)).

The polynomial \(f(x)=8x^{199}+7x^{100}+x^{99}+5x^2+25\) is order of \(x^{199}\) (or \(\Theta(x^{199})\)).

## Relations Between the Relations

- Subset relations between order-of-growth sets.

![](img/c25dfd82fc242c2db53bc942dcad6885_2262_0.png)

## Complexity of Algorithms

## Section Summary

- Time Complexity
- Worst-Case Complexity
- Algorithmic Paradigms
- Understanding the Complexity of Algorithms

## The Complexity of Algorithms

- Given an algorithm, how efficient is this algorithm for solving a problem given input of a particular size? To answer this question, we ask:
  - How much time does this algorithm use to solve a problem?
  - How much computer memory does this algorithm use to solve a problem?
- When we analyze the time the algorithm uses to solve the problem given input of a particular size, we are studying the *time complexity* of the algorithm.
- When we analyze the computer memory the algorithm uses to solve the problem given input of a particular size, we are studying the *space complexity* of the algorithm.

## The Complexity of Algorithms

- In this course, we focus on time complexity. The space complexity of algorithms is studied in later courses.
- We will measure time complexity in terms of the number of operations an algorithm uses and we will use big-O and big-Theta notation to estimate the time complexity.
- We can use this analysis to see whether it is practical to use this algorithm to solve problems with input of a particular size. We can also compare the efficiency of different algorithms for solving the same problem.
- We ignore implementation details (including the data structures used and both the hardware and software platforms) because it is extremely complicated to consider them.

## Time Complexity

- To analyze the time complexity of algorithms, we determine the number of operations, such as comparisons and arithmetic operations (addition, multiplication, etc.). We can estimate the time a computer may actually use to solve a problem using the amount of time required to do basic operations.
- We ignore minor details, such as the “house keeping” aspects of the algorithm.
- We will focus on the *worst-case time* complexity of an algorithm. This provides an upper bound on the number of operations an algorithm uses to solve a problem with input of a particular size.
- It is usually much more difficult to determine the *average case time complexity* of an algorithm. This is the average number of operations an algorithm uses to solve a problem over all inputs of a particular size.
