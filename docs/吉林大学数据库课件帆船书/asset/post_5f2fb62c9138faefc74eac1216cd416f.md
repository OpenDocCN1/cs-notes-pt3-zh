
## Correctness of 3NF Decomposition (Cont’d.)

- Case 2: *B* is in *α*.
  - Since *α* is a candidate key, the third alternative in the definition of 3NF is trivially satisfied.
  - In fact, we cannot show that *γ* is a superkey.
  - This shows exactly why the third alternative is present in the definition of 3NF.

Q.E.D.

## Figure 8.02

| ID | name | salary | dept_name | building | budget |
|---|---|---|---|---|---|
| 22222 | Einstein | 95000 | Physics | Watson | 70000 |
| 12121 | Wu | 90000 | Finance | Painter | 120000 |
| 32343 | El Said | 60000 | History | Painter | 50000 |
| 45565 | Katz | 75000 | Comp. Sci. | Taylor | 100000 |
| 98345 | Kim | 80000 | Elec. Eng. | Taylor | 85000 |
| 76766 | Crick | 72000 | Biology | Watson | 90000 |
| 10101 | Srinivasan | 65000 | Comp. Sci. | Taylor | 100000 |
| 58583 | Califieri | 62000 | History | Painter | 50000 |
| 83821 | Brandt | 92000 | Comp. Sci. | Taylor | 100000 |
| 15151 | Mozart | 40000 | Music | Packard | 80000 |
| 33456 | Gold | 87000 | Physics | Watson | 70000 |
| 76543 | Singh | 80000 | Finance | Painter | 120000 |

## Figure 8.03

| ID | name | street | city | salary |
|---|---|---|---|---|
| ... |  |  |  |  |
| 57766 | Kim | Main | Perryridge | 75000 |
| 98776 | Kim | North | Hampton | 67000 |
| ... |  |  |  |  |

employee

| ID | name |
|---|---|
| ... |  |
| 57766 | Kim |
| 98776 | Kim |
| ... |  |

| name | street | city | salary |
|---|---|---|---|
| ... |  |  |  |
| Kim | Main | Perryridge | 75000 |
| Kim | North | Hampton | 67000 |
| ... |  |  |  |

natural join

| ID | name | street | city | salary |
|---|---|---|---|---|
| ... |  |  |  |  |
| 57766 | Kim | Main | Perryridge | 75000 |
| 57766 | Kim | North | Hampton | 67000 |
| 98776 | Kim | Main | Perryridge | 75000 |
| 98776 | Kim | North | Hampton | 67000 |
| ... |  |  |  |  |

## Figure 8.04

| A | B | C | D |
|---|---|---|---|
| $a_1$ | $b_1$ | $c_1$ | $d_1$ |
| $a_1$ | $b_2$ | $c_1$ | $d_2$ |
| $a_2$ | $b_2$ | $c_2$ | $d_2$ |
| $a_2$ | $b_3$ | $c_2$ | $d_3$ |
| $a_3$ | $b_3$ | $c_2$ | $d_4$ |

## Figure 8.05

| building | room_number | capacity |
|---|---|---|
| Packard | 101 | 500 |
| Painter | 514 | 10 |
| Taylor | 3128 | 70 |
| Watson | 100 | 30 |
| Watson | 120 | 50 |

## Figure 8.06

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_364_0.png)

## Figure 8.14

| dept_name | ID | street | city |
|-----------|----|--------|------|
| Physics | 22222 | North | Rye |
| Physics | 22222 | Main | Manchester |
| Finance | 12121 | Lake | Horseneck |

## Figure 8.15

| dept_name | ID | street | city |
|---|---|---|---|
| Physics | 22222 | North | Rye |
| Math | 22222 | Main | Manchester |

## Figure 8.17

| A | B | C |
| --- | --- | --- |
| a1 | b1 | c1 |
| a1 | b1 | c2 |
| a2 | b1 | c1 |
| a2 | b1 | c3 |

## Chapter 9: Application Design and Development

## Chapter 9: Application Design and Development

- Application Programs and User Interfaces
- Web Fundamentals
- Servlets and JSP
- Application Architectures
- Rapid Application Development
- Application Performance
- Application Security
- Encryption and Its Applications

## APPLICATION PROGRAMS AND USER INTERFACES

- Most database users do *not* use a query language like SQL
- An application program acts as the intermediary between users and the database
  - Applications split into
    - front-end
    - middle layer
    - backend
- Front-end: user interface
  - Forms
  - Graphical user interfaces
  - Many interfaces are Web-based

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_370_0.png)

## APPLICATION ARCHITECTURE EVOLUTION

Three distinct era’s of application architecture

- mainframe (1960’s and 70’s)
- personal computer era (1980’s)
- Web era (1990’s onwards)

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_371_0.png)

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_371_1.png)

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_371_2.png)
