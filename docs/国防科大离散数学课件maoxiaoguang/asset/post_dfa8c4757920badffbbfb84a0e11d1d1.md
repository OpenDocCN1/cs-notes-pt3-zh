
## Example

- Let φ = (p ∨ (q → r))
- Let α = {p ↦ 0, q ↦ 0, r ↦ 1}
- Q: Does α satisfy φ?
  (in symbols: does it hold that α ⊨ φ?)
- A: (0 ∨ (0 → 1)) = (0 ∨ 1) = 1
- Hence, α ⊨ φ.
- Let us now formalize an evaluation process.

## The satisfaction relation (⊨): formalities

⊨ is a relation: ⊨ ⊆ (2^{Prop} × Form)

- Examples:
  - ({a}, a ∨ b) // the assignment α = {a} satisfies a ∨ b
  - ({a,b}, a ∧ b)

⊨ is defined recursively:

- α ⊨ p if α(p) = true (or, p ∈ α)
- α ⊨ ¬φ if α ⊭ φ.
- α ⊨ φ₁ ∧ φ₂ if α ⊨ φ₁ and α ⊨ φ₂
- α ⊨ φ₁ ∨ φ₂ if α ⊨ φ₁ or α ⊨ φ₂
- α ⊨ φ₁ → φ₂ if α ⊨ φ₁ implies α ⊨ φ₂
- α ⊨ φ₁ ↔ φ₂ if α ⊨ φ₁ iff α ⊨ φ₂

## From definition to an evaluation algorithm

### Truth Evaluation Problem

- Given φ ∈ Form and α ∈ 2^{AP(φ)}, does α ⊨ φ ?

```
Eval(φ, α) {
    If φ ≡ p, return α(p).
    If φ ≡ (¬φ₁) return ¬Eval(φ₁, α)
    If φ ≡ (φ₁ ∘ φ₂)
        return Eval(φ₁, α) ∘ Eval(φ₂, α)
}
```

**ALGORITHMIC PERSPECTIVE**

### ‘Eval’ uses polynomial time and space.

## It doesn’t give us more than what we already know...

- Recall our example
  - Let φ = (p ∨ (q → r))
  - Let α = {p ↦ 0, q ↦ 0, r ↦ 1}

Eval(φ, α) = Eval(p, α) ∨ Eval(q → r, α) = 0 ∨ (Eval(q, α) → Eval(r, α)) = 0 ∨ (0 → 1) = 0 ∨ 1 = 1

Hence, α ⊨ φ.

## Satisfiability (SAT) Problem

Given a p, is p satisfiable?

```
SAT(p)
B:=0
for all τ ∈ 2^{AP(p)}
    B = B ∨ Eval(p,τ)
end
return B
```

NP-Complete

## Tautology, Contradiction, Contingency

- Tautology: a statement that’s always true
  - p ∨ ¬p will always be true
- Contradiction: a statement that’s always false
  - p ∧ ¬p will always be false
- Let p be a proposition. Then p ∨ ¬p is a tautology. p ∧ ¬p is a contradiction. p and ¬p are contingencies.

### Definition

A compound proposition that is always true is called a tautology (valid). A compound proposition that is always false is called a contradiction (unsatisfiable). A proposition that is neither a tautology nor a contradiction is called a contingency (satisfiable).

## Possible Worlds and Models

- Logicians typically think in terms of models, which are formally structured worlds with respect to which truth value can be evaluated.
- *m* is a model of a sentence *α* if *α* is true in *m*
- *M(α)* is the set of all models of *α*
- **Possible worlds ~ models**
  - Possible worlds: potentially real environments
  - Models: mathematical abstractions that establish the truth or falsity of every sentence
- **Example:**
  - x + y = 4, where x = #men, y = #women
  - Possible models = all possible assignments of integers to x and y

## Definitions wrt Model

- A **model** of a PL formula A: an interpretation 𝒢 such that A is true in 𝒢: 𝒢(A) = T.
  - A formula is a **tautology** iff **any interpretation is its model**.
  - A formula is a **contradiction** iff **it has no model**.
  - A formula is a **contingency** iff **it has at least one model**.
- A set of formulas {A₁,...,Aₙ} is satisfiable iff there is an interpretation 𝒢 such that 𝒢 is a model of every formula Aᵢ, i = 1,...,n.
  - The interpretation 𝒢 is then **a model of the set {A₁,...,Aₙ}**.

## Set of assignments

- Intuition: a formula specifies a set of truth assignments.
- Function models: Form ↦ 2^{2^{Prop}}
  (a formula ↦ set of satisfying assignments)
- Recursive definition:
  - models(p) = {α | α(p) = 1}, p ∈ Prop
  - models(¬φ₁) = 2^{Prop} − models(φ₁)
  - models(φ₁∧φ₂) = models(φ₁) ∩ models(φ₂)
  - models(φ₁∨φ₂) = models(φ₁) ∪ models(φ₂)
  - models(φ₁→φ₂) = (2^{Prop} − models(φ₁)) ∪ models(φ₂)

## Theorem

Let φ ∈ Form and α ∈ 2^{Prop}, then the following statements are equivalent:

- α ⊨ φ
- α ∈ models(φ)

## Only the projected assignment matters...

- AP(φ) – the Atomic Propositions in φ.
- Clearly AP(φ) ⊆ Prop.
- Let α₁, α₂ ∈ 2^{Prop}, φ ∈ Formula.
- **Lemma:** if α₁|_{AP(φ)} = α₂|_{AP(φ)}, then α₁ ⊨ φ iff α₂ ⊨ φ

![](img/47b87ec6fe4fa238d13429358848c545_66_0.png)

**Corollary:** α ⊨ φ iff α|_{AP(φ)} ⊨ φ

- We will assume, for simplicity, that Prop = AP(φ).
