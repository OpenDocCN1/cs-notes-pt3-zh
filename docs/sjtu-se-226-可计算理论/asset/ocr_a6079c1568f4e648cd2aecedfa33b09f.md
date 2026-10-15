# Undecidability Result

# Theorem

The problem ‘x ∈ Wₓ’ is undecidable.

# Proof

The characteristic function of this problem is given by

c(x) = { 1, if x ∈ Wₓ, 0, if x ∉ Wₓ }

Suppose c(x) was computable. Then the function g(x) defined below would also be computable.

g(x) = { 0, if c(x) = 0, undefined, if c(x) = 1 }

Let m be an index for g. Then

m ∈ Wₘ iff c(m) = 0 iff m ∉ Wₘ.