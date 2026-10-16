# RSA Encryption

+   - To encrypt a message using RSA using a key (n,e) :
+     i. Translate the plaintext message M into sequences of two digit integers representing the letters. Use 00 for A, 01 for B, etc.
+     ii. Concatenate the two digit integers into strings of digits.
+     iii. Divide this string into equally sized blocks of 2N digits where 2N is the largest even number 2525...25 with 2N digits that does not exceed n.
+     iv. The plaintext message M is now a sequence of integers m₁,m₂,...,mₖ.
+     v. Each block (an integer) is encrypted using the function C = Mᵉ mod n.