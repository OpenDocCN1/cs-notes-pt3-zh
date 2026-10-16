# 4.1.2 Subtleties

Sometimes, guess correctly, but somehow the math doesn't seem to work out in the induction.

For example  $T(n) = T(\lfloor n/2 \rfloor) + T(\lceil n/2 \rceil) + 1.$

guess $T(n)=cn$, thne $T(n) \le c\lfloor n/2 \rfloor + c\lceil n/2 \rceil +1 = cn +1$, contradiction.

Usually, it is that the inductive assumption isn't strong enough to prove the detailed bound. How to overcome? (递归假设条件不强)

Revising the guess by subtracting a lower-order term often permits the math to go through. (减去低阶项)