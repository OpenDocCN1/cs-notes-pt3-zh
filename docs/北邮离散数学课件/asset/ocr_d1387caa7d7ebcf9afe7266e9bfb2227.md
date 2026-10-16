# Cryptographic Protocols: Digital Signatures

Adding a *digital signature* to a message is a way of ensuring the recipient that the message came from the purported sender.

+   - Suppose that Alice’s RSA public key is \((n,e)\) and her private key is \(d\). Alice encrypts a plain text message \(x\) using \(E_{(n,e)}(x)=x^d \bmod n\). She decrypts a ciphertext message \(y\) using \(D_{(n,e)}(y)=y^d \bmod n\).
+   - Alice wants to send a message \(M\) so that everyone who receives the message knows that it came from her.
+     1. She translates the message to numerical equivalents and splits into blocks, just as in RSA encryption.
+     2. She then applies her decryption function \(D_{(n,e)}\) to the blocks and sends the results to all intended recipients.
+     3. The recipients apply Alice’s encryption function and the result is the original plain text since \(E_{(n,e)}(D_{(n,e)}(x))=x\).

Everyone who receives the message can then be certain that it came from Alice.