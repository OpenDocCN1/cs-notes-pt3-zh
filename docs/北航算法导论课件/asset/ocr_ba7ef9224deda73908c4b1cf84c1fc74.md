# Why is RSA encryption effective

![](bbox=[0.45, 0.22, 0.93, 0.42])

+   - **RSA public-key cryptosystem**
+     1. Select two large prime numbers p and q, p ≠ q.
+     2. Compute n = pq.
+     3. Compute φ(n) = (p - 1)(q - 1).
+     4. Select a small odd integer e, s.t., gcd(e, φ(n))=1.
+     5. Compute d, by the equation ed ≡ 1(mod φ(n))
+     6. Publish the pair P = (e, n) as his RSA public key.
+     7. Keep secret the pair S = (d, n) as his RSA secret key.

# RSA is secure

S(P(M)) = S( M^e (mod n) ) = M^{ed} (mod n) = ... = M

+   - If factoring n is easy, breaking the RSA cryptosystem is easy.
+   - Conversely, that if factoring large integers is hard, then breaking RSA is hard, is unproven.
+   - After two decades of research, however, no easier method has been found to break the RSA public-key cryptosystem than to factor n.
+   - In fact, the factoring of large integers is surprisingly difficult.