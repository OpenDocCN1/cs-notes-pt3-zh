# Decidable problems concerning regular languages

Proof:

We present a TM N that decides A_NFA :

N="On input <B, w>, where B is a NFA and w is a string:

+   1. Convert NFA B to an equivalent DFA C.

+   2. Run TM M from the last proof on input <C, w>.

+   3. If M accepts, accept; otherwise, reject."