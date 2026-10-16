# Example of Second Principle

+   - Show that every *n*>1 can be written as a product Π *p_i* = *p₁p₂…p_s* of some series of *s* prime numbers.
+     - Let *P(n)*="*n* has that property"

+   - **Base case:** *n*=2, let *s*=1, *p₁*=2.

+   - **Inductive step:** Let *n*≥2. Assume ∀2≤*k*≤*n*: *P(k)*. Consider *n*+1. If it’s prime, let *s*=1, *p₁*=*n*+1. Else *n*+1=*ab*, where 1<*a*≤*n* and 1<*b*≤*n*. Then *a*=*p₁p₂…p_t* and *b*=*q₁q₂…q_u*. Then we have that *n*+1 = *p₁p₂…p_t q₁q₂…q_u*, a product of *s*=*t*+*u* primes.