
## More Equivalence Laws

- *Distributive:*  $p \lor (q \land r) \Leftrightarrow (p \lor q) \land (p \lor r)$
  $p \land (q \lor r) \Leftrightarrow (p \land q) \lor (p \land r)$
- *De Morgan’s:*
  $\lnot(p \land q) \Leftrightarrow \lnot p \lor \lnot q$
  $\lnot(p \lor q) \Leftrightarrow \lnot p \land \lnot q$
- *Trivial tautology/contradiction:*
  $p \lor \lnot p \Leftrightarrow \mathbf{T}$      $p \land \lnot p \Leftrightarrow \mathbf{F}$

![](img/c25dfd82fc242c2db53bc942dcad6885_235_0.png)

## Defining Operators via Equivalences

Using equivalences, we can *define* operators in terms of other operators.

- Exclusive or: $p \oplus q \Leftrightarrow (p \lor q) \land \lnot (p \land q)$
  $p \oplus q \Leftrightarrow (p \land \lnot q) \lor (q \land \lnot p)$
- Implies: $p \rightarrow q \Leftrightarrow \lnot p \lor q$
- Biconditional: $p \leftrightarrow q \Leftrightarrow (p \rightarrow q) \land (q \rightarrow p)$
  $p \leftrightarrow q \Leftrightarrow \lnot (p \oplus q)$

## Tautologies revisited

- We’ve introduced the notion of a tautology using the example $p \lor \lnot p$
- Now, you know more operators, so can formulate many more tautologies, e.g., $(p \lor q) \leftrightarrow \lnot(\lnot p \land \lnot q)$
$(p \rightarrow q) \leftrightarrow (\lnot q \rightarrow \lnot p)$, and so on

## Table 4

# TABLE 4

A Demonstration That p ∨ (q ∧ r) and (p ∨ q) ∧ (p ∨ r) Are Logically Equivalent.

| p | q | r | q ∧ r | p ∨ (q ∧ r) | p ∨ q | p ∨ r | (p ∨ q) ∧ (p ∨ r) |
|---|---|---|-------|-------------|-------|-------|-------------------|
| T | T | T | T | T | T | T | T |
| T | T | F | F | T | T | T | T |
| T | F | T | F | T | T | T | T |
| T | F | F | F | T | T | T | T |
| F | T | T | T | T | T | T | T |
| F | T | F | F | F | T | F | F |
| F | F | T | F | F | F | T | F |
| F | F | F | F | F | F | F | F |

## Constructing New Logical Equivalences

- We can show that two expressions are logically equivalent by developing a series of logically equivalent statements.
- To prove that $A \equiv B$ we produce a series of equivalences beginning with A and ending with B.
  $A \equiv A_1$
  $\vdots$
  $A_n \equiv B$
- Keep in mind that whenever a proposition (represented by a propositional variable) occurs in the equivalences listed earlier, it may be replaced by an arbitrarily complex compound proposition.

## Equivalence Proofs

Example: Show that ¬(p ∨ (¬p ∧ q)) is logically equivalent to ¬p ∧ ¬q

# Solution:

¬(p ∨ (¬p ∧ q)) ≡ ¬p ∧ ¬(¬p ∧ q) by the second De Morgan law

≡ ¬p ∧ [¬(¬p) ∨ ¬q] by the first De Morgan law

≡ ¬p ∧ (p ∨ ¬q) by the double negation law

≡ (¬p ∧ p) ∨ (¬p ∧ ¬q) by the second distributive law

≡ F ∨ (¬p ∧ ¬q) because ¬p ∧ p ≡ F

≡ (¬p ∧ ¬q) ∨ F by the commutative law for disjunction

≡ (¬p ∧ ¬q) by the identity law for F

## EXAMPLE 5

- Show that ¬(p∨(¬ p∧q)) and ¬ p∧ q are logically equivalent.
- 

¬(p∨(¬p∧q)) ⇔ ¬p∧¬(¬p∧q)
⇔ ¬p∧[¬(¬p)∨¬q]
⇔ ¬p∧(p∨¬q)
⇔ (¬p∧p)∨(¬p∧¬q)
⇔ F∨(¬p∧¬q)
⇔ (¬p∧¬q)∨F
⇔ ¬p∧¬q

## An Example Problem

- Check using a symbolic derivation whether $(p \land \lnot q) \rightarrow (p \oplus r) \Leftrightarrow \lnot p \lor q \lor \lnot r.$

$(p \land \lnot q) \rightarrow (p \oplus r)$      [Expand definition of →]
$\Leftrightarrow \lnot(p \land \lnot q) \lor (p \oplus r)$      [Expand defn. of ⊕]
$\Leftrightarrow \lnot(p \land \lnot q) \lor ((p \lor r) \land \lnot(p \land r))$      [DeMorgan’s Law]
$\Leftrightarrow (\lnot p \lor q) \lor ((p \lor r) \land \lnot(p \land r))$      cont.

## Example Continued...

($\neg p \vee q$) $\vee$ (($p \vee r$) $\wedge$ $\neg$($p \wedge r$)) $\Leftrightarrow$ [$\vee$ commutes]
$\Leftrightarrow$ ($q \vee \neg p$) $\vee$ (($p \vee r$) $\wedge$ $\neg$($p \wedge r$)) [$\vee$ is associative]
$\Leftrightarrow$ $q \vee$ ($\neg p \vee$ (($p \vee r$) $\wedge$ $\neg$($p \wedge r$))) [distrib. $\vee$ over $\wedge$]
$\Leftrightarrow$ $q \vee$ ((( $\neg p \vee$ ($p \vee r$)) $\wedge$ ($\underline{\neg p} \vee$ $\neg$($p \wedge r$)))
[assoc.] $\Leftrightarrow$ $q \vee$ ((( $\neg p \vee p$) $\vee r$) $\wedge$ ($\neg p \vee \neg$($p \wedge r$)))
[trivial taut.] $\Leftrightarrow$ $q \vee$ (($\mathbf{T} \vee r$) $\wedge$ ($\neg p \vee \neg$($p \wedge r$)))
[domination] $\Leftrightarrow$ $q \vee$ ($\mathbf{T} \wedge$ ($\neg p \vee \neg$($p \wedge r$)))
[identity]      $\Leftrightarrow$ $q \vee$ ($\neg p \vee \neg$($p \wedge r$)) $\Leftrightarrow$ cont.
