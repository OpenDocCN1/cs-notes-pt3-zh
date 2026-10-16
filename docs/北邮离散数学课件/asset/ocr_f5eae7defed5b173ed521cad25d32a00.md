# # Shift Cipher

**Example 2:** Decrypt the message “LEWLYPLUJL PZ H NYLHA ALHJO L Y” that was encrypted using the shift cipher with *k* = 7.

**Solution:** Replace each letter with the corresponding element of \(\mathbb{Z}_{26}\).

11 4 22 11 24 15 11 20 9 11   15 25   7 13 24 11 7 0   0 11 7 9 14 11 24.

Shift each of the numbers by \(-k=-7\) modulo 26, yielding

4 23 15 4 17 8 4 13 2 4   8 18   0   6 17 4 0 19   19 4 0 2 7 4 17.

Translating the numbers back to letters produces the decrypted message

> > “EXPERIENCE IS A GREAT TEACHER.”