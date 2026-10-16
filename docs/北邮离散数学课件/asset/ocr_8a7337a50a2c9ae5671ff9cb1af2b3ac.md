# # Decoding function

Let e be an (m, n) encoding function and let
d be an (n, m) decoding function
associated with e.

The pair (e, d) is said to **correct k or fewer errors**

if whenever x = e(b) is transmitted correctly or
with k or fewer errors and x<sub>t</sub> is received, then
d(x<sub>t</sub>) = b. Thus x<sub>t</sub> is decoded as the correct
message b.