
# Quantifiers

- example: domain x is real numbers. P(x) is x > -1.
  - ∀ x P(x)  (F)  *counter-example : x=-2*
  - ∃ x P(x)  (T)

- example: domain is positive real numbers, P(x) is x>-1.
  - ∀ x P(x)  (T)
  - ∃ x P(x)  (T)

# Binding Variables

- A variable is _bound_ if it has a value or a quantifier is "acting" on it.
- A statement can only become a proposition if all variables are bound.
- example: ∃ x P(x,y), x is bound, y is free.

# Scope of a quantifier

- The *scope* of a quantifier is the part of the statement on which it is acting.
- example

![](img/596a7ad0af4b255f7c4ff59547a2dbb3_43_0.png)

# Negation of a quantified Prop.

- We can also negate propositions with quantifiers.
- Two important equivalences:
  - ¬∀x P(x) ≡ ∃x ¬P(x), It is not the case that for all x P(x) is true ≡ there must be an x for which P(x) is not true
  - ¬∃x P(x) ≡ ∀x ¬P(x), It is not true that there exists an x for which P(x) is true ≡ P(x) must be false for all x

# Using Predictions and Quantifiers

- Translation sentence into logical expression
- Example: every students in this class has studied c language
  - ∀ x C(x) the universe of discourse for x is the students in this class
  - ∀ x (S(x) →C(x)) the universe of discourse for x is all the people
  - ∀ x (S(x) →L(x, c))

# Using Predictions and Quantifiers

- Logic programming
  - Prolog language
  - Facts and rules
  - Example:
    - instructor (john, math202)
    - enrolled (tom, math202)
    - enrolled (jack, math202)
    - teacher (P,S) :- instructor (P,C), enrolled (S,C)
    - ?enrolled (tom, math202)      yes
    - ?enrolled (X, math202)
    - ?teacher (X, tom)

# homework2

(1) Use 2 ways to prove that

\[(p \lor q) \land (\neg p \lor r) \to (q \lor r)\]

is a tautology

# homework2

(2) Page 37, No.6,8

*Page 47, No.11,16 ver6*

- No.11: let P(x) be the statement “x=x²”, if the domain consists of the integers, what are the truth values? P(0); P(1); P(2); P(-1); ∃x P(x); ∀x P(x)

- No.16: determine the truth value of each statements if the domain consists of real number? ∃x(x²=2); ∃x(x²=-1); ∀x(x²+2≥1); ∀x(x²≠x)

# homework2

(3) Page 39, No.21, 22

*Page 49, No.41,43   verb6*

No. 41: Express each of these system specifications

- a) At least one mail message, among the nonempty set of messages, can be saved if there is a disk with more than 10 kilobytes of free space
- b) whenever there is an active alert, all queued messages are transmitted.
- c) The diagnostic monitor tracks the status of all systems except the main console
- d) each participant on the conference call whom the host the call did not put on a special list was billed

# homework2

(3)

- No. 43: Determine whether ∀x(P(x) → Q(x)) and ∀xP(x) → ∀xQ(x) are logically equivalent. Justify your answer.

# Quiz

- How to prove the equivalence of two logical statements
- Determine whether ∃x(P(x) → Q(x)) and ∃xP(x) → ∃xQ(x) are logically equivalent. Justify your answer.
- ¬(∀x∃y P(x) → ¬Q(y))
  let the Negation act on the predicts directly

# Nested Quantifiers

- **Nested Quantifier:** *Quantifier that appears within the scope of another quantifier*
- Examples: x,y,z are real numbers
  - ∀ x ∃ y (x+y=0)
  - ∀ x ∀ y ∀ z (x+(y+z) = (x+y)+z)
  - ∀ x ∀ y (x>0) ∧ (y<0) → (xy<0)
    - For all x and for all y if x is positive and y is negative then their product must be negative.
    - The product of a positive and a negative real number is negative.

# Using nested quantifiers

- Translate this sentence into a logical expressions.
  - "If a person is female and is a parent, then she is someone’s mother."
- F(x) is "x is female", P(x) is "x is someone’s parent", M(x,y), "x is the mother of y"
  - ∀x ∃y (F(x) ∧ P(x)) → M(x,y)
