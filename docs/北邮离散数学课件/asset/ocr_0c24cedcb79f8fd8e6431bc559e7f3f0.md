# Linear Congruences

**Definition:** A congruence of the form
$a x \equiv b(\mod m)$, 
where $m$ is a positive integer, $a$ and $b$ are integers, and $x$ is a variable, is called a *linear congruence*.

+   - The solutions to a linear congruence $a x \equiv b(\mod m)$ are all integers $x$ that satisfy the congruence.

**Definition:** An integer $\bar{a}$ such that $\bar{a} a \equiv 1(\mod m)$ is said to be an *inverse* of $a$ modulo $m$.
**Example:** 5 is an inverse of 3 modulo 7 since $5 \cdot 3 = 15 \equiv 1(\mod 7)$

+   - One method of solving linear congruences makes use of an inverse $\bar{a}$, if it exists. Although we can not divide both sides of the congruence by $a$, we can multiply by $\bar{a}$ to solve for $x$.