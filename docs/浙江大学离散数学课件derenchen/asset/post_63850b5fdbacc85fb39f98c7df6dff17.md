

## Example 6 Find the prime factorization of 7007.

Solution: first perform divisions of 7007 by successive primes, beginning with 2. None of 2, 3 and 5 divides 7007. However, 7 divides 7007, with 7007/7=1001. Next, divide 1001 by successive prime beginning with 7, 7 also divides 1001, since 1001/7 = 143. Continue by dividing 143 by successive prime beginning with 7, 7 does not divide 143, 11 does divide 143, 143/11=13, 13 is a prime so

7007=7×7 × 11 × 13=7²× 11 × 13

## 定理4（欧几里德定理）

所有质数组成的集合是一个无限集。

证明：若质数是有限的，则可将它们按顺序一个不漏地记为

p₁<p₂<...<pₖ，令n= p₁·p₂·...· pₖ+1，则n或者是个质数，如果n不是质数，则由算术基本定理，则它可以表示成质数的积，它的质因子不可能是p₁， p₂， ...， pₖ之一，这与p₁， p₂， ...， pₖ是所有的质数矛盾。

## Definition 4

Let a and b be integers, not both zero. The largest integer d such that d | a and d | b is called the greatest common divisor of a and b. The greatest common divisor of a and b is denoted by gcd(a,b). Usually simply denoted by (a,b)

The greatest common divisor of two integers, not both zero, exists because the set of common divisors of these integers is finite. One way to find the greatest common divisor of two integers is to find all the positive common divisors of both integers and then take the largest divisor. This is done in the following examples. Later, a more efficient method of finding greatest common divisors will be given.

## Definition 5

The integers a and b are relatively prime if their greatest common divisor is 1

for example 7, 12 and 105, 106

But 105 and 45 are not relatively prime

## Definition 6

The integers a₁, a₂, ... aₙ are pairwise relatively prime, if gcd(aᵢ, aⱼ)=1 whenever 1≤i<j ≤n

![](img/5123c27d7478faaa822d0f1f02fc503f_533_0.png)

Another way to find gcd(a,b) is to use the prime factorizations of a and b. Suppose that the prime factorization of integers a and b, neither equal to zero, are

$$a=p_1^{a_1}p_2^{a_2}\cdots p_n^{a_n}\qquad b=p_1^{b_1}p_2^{b_2}\cdots p_n^{b_n}$$

Where each exponent is zero or positive integer.

$$\operatorname{Gcd}(a,b)=p_1^{\min(a_1,b_1)}p_2^{\min(a_2,b_2)}\cdots p_n^{\min(a_n,b_n)}\tag{2.3.1}$$

$$120=2^3\cdot3\cdot5,\quad 500=2^2\cdot5^3;\quad 2^2\cdot3^0\cdot5^3$$

Gcd(120,500)=2^min(3,2)·3^min(1,0)·5^min(1,3)=2²·3⁰·5¹=20

例 金库内有3根同样粗细的金条，分别长135、243和558（单位英寸）。现在要把它们截成相等的小段，要求小段要最长。问一共可以把这些金条分成几段，每段几英寸。

解:135=3³ · 5, 243=3³, 558=2 · 3² · 31

gcd(135,243,558)=2⁰ · 3² · 5⁰ · 31⁰=9

## Definition 7

The least common multiple of the positive integer a and b is the smallest integer that is divisible by both a and b. it is denoted by lcm(a,b). Simply denote by [a,b]

It is obviously that lcm(a,b) ≤ ab.

Example lcm(4,6)=12

Like gcd(a,b), if have got the prime factorization of a and b, then lcm(a,b) is given by

## Lcm(a,b)= \( p_1^{max(a_1, b_1)} p_2^{max(a_2, b_2)} \cdots p_n^{max(a_n, b_n)} \) (2.3.2)

Theorem 5 Let a and b be positive integers,

Then \( ab = \text{gcd}(a,b) \times \text{lcm}(a,b) \)

Proof: from the formula (2.3.1) and (2.3.2), this conclusion is obvious.

注:另一种证明法: 首先a/(a,b), b/(a,b), 及[a,b]/a, [a,b]/b 都是整数.

## Algorithms 算法

由于ab/(a,b)=a·b/(a,b),因此a| ab/(a,b), b| ab/(a,b), 从而
ab/(a,b)是a,b的公倍数,而[a,b]是a,b的最小公倍数,故
ab/(a,b) ≥[a,b]. 即

ab≥[a,b] (a,b) . (2.3.3)

而另一方面,ab/[a,b] | a, ab/[a,b] | b, 说明ab/[a,b] 是a和b
的公约数, 而(a,b)是a,b的最大公约数, 因此
(a,b) ≥ab/[a,b],即

ab≤(a,b)[a,b] (2.3.4)

## Modular arithmetic (同余)

Definition 8. Let a be an integer and m be a positive integer, we denote by a mod m the remainder when a is divided by m.

For example 5 mod 3 = 2

Definition 9. If a and b are integers and m is a positive integer, then a is congruent to b modulo m if m divides a-b, we denote it by a≡b(mod m)

![](img/5123c27d7478faaa822d0f1f02fc503f_539_0.png)

![](img/5123c27d7478faaa822d0f1f02fc503f_539_1.png)

## Theorem 6

Let m be a positive integer. The integers a and b are congruent modulo m if and only if there is an integer k such that a=b+km.

**Proof:** If a≡b(mod m), then m ∣ (a − b). This means that there is an integer k such that a − b=km, so that a=b+km. Conversely, if there is an integer k such that a=b+km, then km=a − b. Hence, m divides a − b, so that a≡b(mod m).

