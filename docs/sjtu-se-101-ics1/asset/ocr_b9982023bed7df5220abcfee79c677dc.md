# Signed Addition

+   - Functionality
+     - True sum requires w+1 bits
+     - Drop off MSB
+     - Treat remaining bits as 2's comp. integer

Tadd(u,v) = { u + v − 2^w,    TMax_w < u + v (PosOver)
                u + v,      TMin_w ≤ u + v ≤ TMax_w
                u + v + 2^w, u + v < TMin_w (NegOver) }