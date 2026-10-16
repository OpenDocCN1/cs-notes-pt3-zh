# Caesar Cipher

Julius Caesar created secret messages by shifting each letter three letters forward in the alphabet (sending the last three letters to the first three letters). For example, the letter B is replaced by the letter E and the letter X is replaced by A. This process of making a message secret is an example of *encryption*.

Here is how the encryption process works:

+   - Replace each letter by an integer from \(\mathbb{Z}_{26}\), that is an integer from 0 to 25 representing one less than its position in the alphabet.
+   - The encryption function is \(f(p)=(p+3)\bmod 26\). It replaces each integer \(p\) in the set \(\{0,1,2,\ldots,25\}\) by \(f(p)\) in the set \(\{0,1,2,\ldots,25\}\).
+   - Replace each integer \(p\) by the letter with the position \(p+1\) in the alphabet.

**Example:** Encrypt the message “MEET YOU IN THE PARK” using the Caesar cipher.

**Solution:** 12 4 4 19   24 14 20   8 13   19 7 4   15 0 17 10.

Now replace each of these numbers \(p\) by \(f(p)=(p+3)\bmod 26\).

15 7 7 22   1 17 23   11 16   22 10 7   18 3 20 13.

Translating the numbers back to letters produces the encrypted message “PHHW BRX LQ WKH SDUN.”

![](bbox=[0.8, 0.024, 0.927, 0.271])