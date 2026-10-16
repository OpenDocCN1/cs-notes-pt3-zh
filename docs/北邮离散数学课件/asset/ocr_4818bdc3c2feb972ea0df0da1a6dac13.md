# # The RSA Cryptosystem

• A public key cryptosystem, now known as the RSA system was introduced in 1976 by three researchers at MIT.

![](bbox=[0.528, 0.021, 0.624, 0.17])

**Clifford Cocks**  
(Born 1950)

![](bbox=[0.257, 0.421, 0.353, 0.568])

Ronald Rivest  
(Born 1948)

![](bbox=[0.566, 0.411, 0.659, 0.56])

Adi Shamir  
(Born 1952)

![](bbox=[0.866, 0.411, 0.961, 0.56])

Leonard  
Adelman  
(Born 1945)

• It is now known that the method was discovered earlier by Clifford Cocks, working secretly for the UK government.

• The public encryption key is $(n,e)$, where $n=pq$ (the modulus) is the product of two large (200 digits) primes $p$ and $q$, and an exponent $e$ that is relatively prime to $(p−1)(q−1)$. The two large primes can be quickly found using probabilistic primality tests, discussed earlier. But $n=pq$, with approximately 400 digits, cannot be factored in a reasonable length of time.