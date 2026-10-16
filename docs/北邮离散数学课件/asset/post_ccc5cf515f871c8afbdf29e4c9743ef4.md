
## Another Fun Example

- Suppose that next June, the Marlins baseball team plays at least 1 game a day, but ≤45 games total. Show there must be some sequence of consecutive days in June during which they play *exactly* 14 games.
  - **Proof:** Let $a_j$ be the number of games played on or before day $j$. Then, $a_1, ..., a_{30} \in \mathbf{Z}^+$ is a sequence of 30 distinct integers with $1 \le a_j \le 45$. Therefore $a_1+14, ..., a_{30}+14$ is a sequence of 30 distinct integers with $15 \le a_j+14 \le 59$. Thus, $(a_1, ..., a_{30}, a_1+14, ..., a_{30}+14)$ is a sequence of 60 integers from the set $\{1,..,59\}$. By the Pigeonhole Principle, two of them must be equal, but $a_i \neq a_j$ for $i \neq j$. So, $\exists i j: a_i = a_j+14$. Thus, 14 games were played on days $a_j+1, ..., a_i$.

## Baseball problem illustrated

- Example of {a_i}: Note all elements are distinct.
  - 1, 2, 4, 5, 7, 8, 10, 11, 13, 14, 16, 17, 19, 21, 22, 23, 25, 27, 29, 30, 31, 33, 34, 36, 37, 39, 40, 41, 43, 45
  - Then {a_i+14} is the following sequence
    15, 16, 18, 19, 21, 22, 24, 25, 27, 28, 30, 32, 33, 35, 36, 37, 39, 41, 43, 44, 45, 47, 48, 50, 51, 53, 54, 55, 57, 59

- In any 60 integers from 1-59 there must be some duplicates, indeed we find the following ones:
  - 16, 19, 21, 22, 25, 27, 30, 33, 36, 37, 39, 41, 43, 45

> Thus, for example, exactly 14 games were played during days 3 to 11:
> 2+1+2+1+2+1+2+1+2

## Generalized Pigeonhole Principle

- If *N* objects are assigned to *k* places, then at least one place must be assigned at least ⌈*N/k*⌉ objects.
- *E.g.*, there are *N*=280 students in this class. There are *k*=52 weeks in the year.
  - Therefore, there must be at least 1 week during which at least ⌈280/52⌉=⌈5.38⌉=6 students in the class have a birthday.

## Proof of G.P.P.

- By contradiction. Suppose every place has < ⌈N/k⌉ objects, thus ≤ ⌈N/k⌉−1.
- Then the total number of objects is at most
  $$k\left(\left\lceil\frac{N}{k}\right\rceil-1\right)<k\left(\left(\frac{N}{k}+1\right)-1\right)=k\left(\frac{N}{k}\right)=N$$
- So, there are less than N objects, which contradicts our assumption of N objects! □

## G.P.P. Example

- Given: There are 280 students in the class.
  - Without knowing anybody’s birthday, what is the largest value of $n$ for which we can prove using the G.P.P. that at least $n$ students must have been born in the same month?
- Answer:

⌈280/12⌉ = ⌈23.3⌉ = 24

## Example 7

- A) How many cards must be selected from a standard deck of 52 cards to guarantee that at least three cards of the same suit are chosen?
- B) How many must be selected to guarantee that at least three hearts are selected?

## Some elegant application

- Example.11 Show that among any n+1 positive integers not exceeding 2n there must be an integer that divides one of the other integers.
- Example 13 Assume that in a group of six people, each pair of individuals consists of two friends or two enemies. Show that there are either three mutual friends or three mutual enemies in the group.
- Ramsy number

## Theorem 3

- Every sequence of n²+1 distinct real numbers contains a subsequence of length n+1 that is either strictly increasing or strictly decreasing.
- 8, 11, 9, 1, 4 ,6, 12, 10, 5, 7
- 1 4 6 10

## Permutations ( § 6.3 )

- A *permutation* of a set $S$ of objects is a sequence that contains each object in $S$ exactly once.
  - An ordered arrangement of $r$ distinct elements of $S$ is called an $r$-permutation of $S$.
- The number of $r$-permutations of a set with $n=|S|$ elements is
  $P(n,r) = n(n-1)...(n-r+1) = n!/(n-r)!$

## Permutation Example

- A terrorist has planted an armed nuclear bomb in your city, and it is your job to disable it by cutting wires to the trigger device. There are 10 wires to the device. If you cut exactly the right three wires, in exactly the right order, you will disable the bomb, otherwise it will explode! If the wires all look the same, what are your chances of survival?

P(10,3) = 10·9·8 = 720, so there is a 1 in 720 chance that you’ll survive!
