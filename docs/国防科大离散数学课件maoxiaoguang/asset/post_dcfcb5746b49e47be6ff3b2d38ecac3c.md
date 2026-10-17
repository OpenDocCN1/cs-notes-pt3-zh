
## Proofs of functional completeness

- Transition to the system {¬, ∧} or {¬, ∨}:
  - A ∧ B ⇔ ¬(¬A ∨ ¬B),
  - A ∨ B ⇔ ¬(¬A ∧ ¬B)
- The system {¬, ∧, ∨} is sufficient according to the above statement.
- Transition to the system {¬, →}:
  - A ∨ B ⇔ ¬A → B,
  - A ∧ B ⇔ ¬(A → ¬B)
- Transition to the system {↑} or {↓}:
  - ¬A ⇔ A ↑ A, A ∧ B ⇔ (A ↑ B) ↑ (A ↑ B) (↑ is NAND),
  - ¬A ⇔ A ↓ A, A ∨ B ⇔ (A ↓ B) ↓ (A ↓ B) (↓ is NOR).

## Existence of normal forms

Findings:

### CNF

- (p ∨ ¬q) ∧ (q ∨ ¬r) is F **iff**
- at least one elementary disjunction is F **iff**
- all literals in that elementary disjunction are F

### DNF

- (p ∧ ¬q) ∨ (q ∧ ¬r) is T **iff**
- at least one elementary conjunction is T **iff**
- all literals in that elementary conjunction are T

## A simple example

**Wff:** ¬(p → q)

**CNF:** (¬p ∨ ¬q) ∧ (p ∨ ¬q) ∧ (p ∨ q)

**DNF:** (p ∧ ¬q)

If we construct a CCNF (CDNF) from a truth table, we take into account only those rows where the function has the value F (T), and construct CED (CEC) in such a way that the CED (CEC) is false (true).

| p | q | ¬(p → q) | CNF | DNF |
| --- | --- | --- | --- | --- |
| T | T | F | ¬p ∨ ¬q |  |
| T | F | T |  | p ∧ ¬q |
| F | T | F | p ∨ ¬q |  |
| F | F | F | p ∨ q |  |

## Further example

Find CCNF and CDNF for the formula A?

| p | q | r | A |
| --- | --- | --- | --- |
| F | F | F | T |
| F | F | T | F |
| F | T | F | T |
| F | T | T | T |
| T | F | F | F |
| T | F | T | T |
| T | T | F | F |
| T | T | T | F |

## Existence of normal forms

- Each formula which is not a contradiction has a CDNF (complete disjunctive normal form).
  - A contradiction does not have a CDNF.
- Each formula which is not a tautology has a CCNF (complete conjunctive normal form).
  - A tautology does not have a CCNF.

## Example

Assume: ¬(P → Q) ∨ (R → P)

- **Eliminate ↔, →**: ¬(¬P ∨ Q) ∨ (¬R ∨ P)
- **Reduce the scope of ¬ through de Morgan's laws and double negation**: (P ∧ ¬Q) ∨ (¬R ∨ P)
- **Convert to CNF using the distributive laws and laws for flatten**: (P ∨ ¬R) ∧ (¬Q ∨ ¬R ∨ P)

## Conversion to DNF with ⇔

1. Eliminate ⇔, replacing α ⇔ β with (α → β) ∧ (β → α).
2. Eliminate →, replacing α → β with ¬α ∨ β.
3. Move ¬ inwards using de Morgan's rules and double-negation.
   - ¬(α ∨ β) ⇔ ¬α ∧ ¬β
   - ¬(α ∧ β) ⇔ ¬α ∨ ¬β
   - ¬¬α ⇔ α
4. Apply distributive law (∧ over ∨) and flatten.
   - α ∧ (β ∨ γ) ⇔ (α ∧ β) ∨ (α ∧ γ)

## Decision approaches

- Satisfiability (SAT) problem: Determine whether a sentence in normal forms (CNF or DNF) is satisfiable (i.e. can evaluate to true).

Not limited to:

- Complete normal forms: CCNF, CDNF

  (P ∨ ¬R ∨ Q) ∧ (P ∨ ¬R ∨ ¬Q) ∧ (¬Q ∨ ¬R ∨ P)?

- With the resolution rule

## Conversion to CNF with ⇔

1. Eliminate ⇔, replacing α ⇔ β with (α → β) ∧ (β → α).
2. Eliminate →, replacing α → β with ¬α ∨ β.
3. Move ¬ inwards using de Morgan's rules and double-negation.
   - ¬(α ∨ β) ⇔ ¬α ∧ ¬β
   - ¬(α ∧ β) ⇔ ¬α ∨ ¬β
   - ¬¬α ⇔ α
4. Apply distributive law (∨ over ∧) and flatten.
   - α ∨ (β ∧ γ) ⇔ (α ∨ β) ∧ (α ∨ γ)
5. Supplementing missing literals.
   - α ⇔ (α ∨ ¬γ) ∧ (α ∨ γ)

## Example

Assume: ¬(P → Q) ∨ (R → P)

- **Eliminate ↔, →**: ¬(¬P ∨ Q) ∨ (¬R ∨ P)
- **Reduce the scope of ¬ through de Morgan's laws and double negation**: (P ∧ ¬Q) ∨ (¬R ∨ P)
- **Convert to CNF using the distributive laws and laws for flatten**: (P ∨ ¬R) ∧ (¬Q ∨ ¬R ∨ P)
- **Convert to CCNF by supplementing missing literals**: (P ∨ ¬R ∨ Q) ∧ (P ∨ ¬R ∨ ¬Q) ∧ (¬Q ∨ ¬R ∨ P)
