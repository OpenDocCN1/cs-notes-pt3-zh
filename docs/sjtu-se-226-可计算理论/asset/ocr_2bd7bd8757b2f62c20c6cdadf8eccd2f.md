# Normal Form Theorem

Normal Form Theorem. M(\bar{x}) is partially decidable iff there is a primitive recursive predicate R(\bar{x}, y) such that M(\bar{x}) iff ∃y.R(\bar{x}, y).

Proof. If R(\bar{x}, y) is primitive recursive and M(\bar{x}) ⇔ ∃y.R(\bar{x}, y), then the computable function “if μyR(\bar{x}, y) then 1 else ↑” is the partial characteristic function of M(\bar{x}).