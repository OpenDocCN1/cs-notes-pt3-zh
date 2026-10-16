# Concurrency Control (Cont.)

A non-conflict-serializable schedule that preserves the sum of A + B

| T1 | T2 |
|---|---|
| read(A) | |
| A : A − 50 | |
| write(A) | |
| | read(B) |
| | B : B − 10 |
| read(B) | write(B) |
| B : B + 50 | |
| write(B) | |
| | read(A) |
| | A : A + 10 |
| | write(A) |