# Check Digits:ISBNs

Books are identified by an International Standard Book Number (ISBN-10), a 10 digit code. The first 9 digits identify the language, the publisher, and the book. The tenth digit is a check digit, which is determined by the following congruence

```
x₁₀ ≡ Σ (i=1 to 9) i xᵢ (mod 11).
```

The validity of an ISBN-10 number can be evaluated with the equivalent Σ (i=1 to 10) i xᵢ ≡ 0 (mod 11).

+   a. Suppose that the first 9 digits of the ISBN-10 are 007288008. What is the check digit?
+   b. Is 084930149X a valid ISBN10?

# Solution:

+   a. X₁₀ ≡ 1·0 + 2·0 + 3·7 + 4·2 + 5·8 + 6·8 + 7·0 + 8·0 + 9·8 (mod 11).
+   X₁₀ ≡ 0 + 0 + 21 + 8 + 40 + 48 + 0 + 0 + 72 (mod 11).
+   X₁₀ ≡ 189 ≡ 2 (mod 11). Hence, X₁₀ = 2.

+   b. 1·0 + 2·8 + 3·4 + 4·9 + 5·3 + 6·0 + 7·1 + 8·4 + 9·9 + 10·10 =
+   0 + 16 + 12 + 36 + 15 + 0 + 7 + 32 + 81 + 100 = 299 ≡ 2 ≠ 0 (mod 11)
+   Hence, 084930149X is not a valid ISBN-10.

X is used for the digit 10.

A single error is an error in one digit of an identification number and a transposition error is the accidental interchanging of two digits. Both of these kinds of errors can be detected by the check digit for ISBN-10. (see text for more details)