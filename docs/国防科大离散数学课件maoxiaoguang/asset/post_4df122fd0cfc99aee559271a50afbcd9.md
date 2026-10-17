
## Extension of ⊨ to sets of assignments

+   Let φ ∈ Form
+   Let T be a set of assignments, i.e., T ⊆ 2^Prop

T ⊨ φ if T ⊆ models(φ)

i.e., ⊨ ⊆ 2^Prop × Form

## Extension of ⊨ to formulas

+   ⊨ ⊆ 2^Form × Form
+   Definition. Let Γ, φ be prop. formulas.

Γ ⊨ φ
iff models(Γ) ⊆ models(φ)
iff for all α ∈ 2^Prop
    if α ⊨ Γ then α ⊨ φ

Example:

p , q ⊨ p ∨ r

## Extension of ⊢ to formulas

+   ⊢ ⊆ ²Form × ²Form
+   **Definition.** Let Γ₁, Γ₂ be prop. formulas.

Γ₁ = Γ₂
iff models(Γ₁) ⊆ models(Γ₂)
iff for all α ∈ ²Prop
if α ⊢ Γ₁ then α ⊢ Γ₂

## 0812235

## Logic and Algebra

## Ch 1.2 Propositional Equivalences

## Fall 2010

## Mao Xiaoguang

## Equivalences

+   A logical equivalence means that the two sides always have the same truth values
+   Symbol is ⇔ or ≡ (we’ll use ⇔)
+   REMARK: The symbol ⇔ is not a logical connective since p ≡ q is not a compound proposition.

## Definition

The propositions p and q are called logically equivalent if p ↔ p is a tautology. We write p ⇔ q when p and q are logically equivalent.

## Examples

▣ Identity law    p ∧ T ⇔ p

| *p* | T | *p*∧T |
|---|---|---|
| T | T | T |
| F | T | F |

▣ Commutative law    p ∧ q ⇔ q ∧ p

| p | q | p∧q | q∧p |
|---|---|---|---|
| T | T | T | T |
| T | F | F | F |
| F | T | F | F |
| F | F | F | F |

## Truth Table Solution

□ (p → r) ∨ (q → r) ⇔ (p ∧ q) → r ?

| p | q | r | p→r | q→r | (p→r)∨(q→r) | p∧q | (p∧q)→r |
|---|---|---|-----|-----|-------------|-----|----------|
| T | T | T | T   | T   | T           | T   | T        |
| T | T | F | F   | F   | F           | T   | F        |
| T | F | T | T   | T   | T           | F   | T        |
| T | F | F | F   | T   | T           | F   | T        |
| F | T | T | T   | T   | T           | F   | T        |
| F | T | F | T   | F   | T           | F   | T        |
| F | F | T | T   | T   | T           | F   | T        |
| F | F | F | T   | T   | T           | F   | T        |

## Logical Equivalences

| p ∧ T ⇔ p | Identity Laws | (p ∨ q) ∨ r ⇔ p ∨ (q ∨ r) | Associative laws |
| p ∨ T ⇔ T | Domination Law | p ∨ (q ∧ r) ⇔ (p ∨ q) ∧ (p ∨ r) | Distributive laws |
| p ∧ F ⇔ F | Domination Law | p ∧ (q ∨ r) ⇔ (p ∧ q) ∨ (p ∧ r) | Distributive laws |
| p ∨ p ⇔ p | Idempotent Laws | ¬(p ∧ q) ⇔ ¬p ∨ ¬q | De Morgan's laws |
| p ∧ p ⇔ p | Idempotent Laws | ¬(p ∨ q) ⇔ ¬p ∧ ¬q | De Morgan's laws |
| ¬(¬p) ⇔ p | Double Negation law | p ∨ (p ∧ q) ⇔ p | Absorption laws |
| p ∨ q ⇔ q ∨ p | Commutative Laws | p ∨ ¬p ⇔ T | Negation laws |
| p ∧ q ⇔ q ∧ p | Commutative Laws | p ∧ ¬p ⇔ F | Negation laws |
| p → q ⇔ ¬p ∨ q | Definition of Implication | p ↔ q ⇔ (p → q) ∧ (q → p) | Definition of Biconditional |

## Proof using Logical Equivalence

(p → r) ∨ (q → r)

⇔ (¬ p ∨ r) ∨ (¬ q ∨ r)    Definition of implication

⇔ ¬ p ∨ r ∨ ¬ q ∨ r    Associative

⇔ ¬ p ∨ ¬ q ∨ r ∨ r    Commutative

⇔ (¬ p ∨ ¬ q) ∨ (r ∨ r)    Associative

⇔ ¬ (p ∧ q) ∨ r    De Morgan, Idempotent

⇔ (p ∧ q) → r    Definition of implication

## Example

Show that (p ∧ q) → (p ∨ q) is a Tautology.

(Proof)

```
(p ∧ q) → (p ∨ q)
⇔ ¬(p ∧ q) ∨ (p ∨ q) Implication
⇔ (¬p ∨ ¬q) ∨ (p ∨ q) De Morgan
⇔ (¬p ∨ p) ∨ (¬q ∨ q) Commutative, Associative
⇔ T ∨ T Negation
⇔ T Identity
```

## F8T2235

## Logic and Algebra

## Decision Problem in PL

Fall 2010

Mao Xiaoguang

## A Famous Problem in Computer Science

+   We have shown how to use propositional logic to write system specifications.
+   In real world, there may be hundreds, even thousands of propositions in the requirements. How to find proper truth values to propositions such that all requirements are satisfied. This problem is called the satisfiability problem.
+   Since there are so many propositions, one would write a program to find a solution for us.
+   However, if there are 300 propositions in the specification, a brute-force method may try 2^300 possible combinations. It is worth noting that 2^300 ≈ 10^90 but the number of particles in our universe is roughly 10^87. It doesn't sound "efficient".
+   Whether there is an "efficient" way to solve the problem is the famous P=NP? problem.
