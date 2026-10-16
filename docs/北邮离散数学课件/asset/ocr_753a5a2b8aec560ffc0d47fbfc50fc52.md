# RSA Decryption

+   - **Example:** The message 0981 0461 is received. What is the decrypted message if it was encrypted using the RSA cipher from the previous example.
+   
+     **Solution:** The message was encrypted with *n* = 43·59 and exponent 13. An inverse of 13 modulo 42·58 = 2436 (*exercise 2 in Section 4.4*) is *d* = 937.
+   
+     - To decrypt a block C, *M* = C⁹³⁷ mod 2537.
+     - Since 0981⁹³⁷ mod 2537 = 0704 and 0461⁹³⁷ mod 2537 = 1115, the decrypted message is 0704 1115. Translating back to English letters, the message is **HELP**.