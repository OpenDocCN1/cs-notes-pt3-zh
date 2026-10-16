

## Affine Ciphers

- Shift ciphers are a special case of *affine ciphers* which use functions of the form
  $f(p) = (ap + b) \mod 26,$
  where $a$ and $b$ are integers, chosen so that $f$ is a bijection.
  The function is a bijection if and only if gcd$(a,26) = 1.$

## Cryptanalysis of Affine Ciphers

- The process of recovering plaintext from ciphertext without knowledge both of the encryption method and the key is known as *cryptanalysis* or *breaking codes*.
- An important tool for cryptanalyzing ciphertext produced with a affine ciphers is the relative frequencies of letters. The nine most common letters in the English texts are E 13%, T 9%, A 8%, O 8%, I 7%, N 7%, S 7%, H 6%, and R 6%.
- To analyze ciphertext:
  - Find the frequency of the letters in the ciphertext.
  - Hypothesize that the most frequent letter is produced by encrypting E.
  - If the value of the shift from E to the most frequent letter is *k*, shift the ciphertext by −*k* and see if it makes sense.
  - If not, try T as a hypothesis and continue.

## Cryptanalysis of Affine Ciphers

- **Example:** We intercepted the message “ZNK KGXRE HOXJ MKZY ZNK CUXS” that we know was produced by a shift cipher. Let’s try to cryptanalyze.

- **Solution:** The most common letter in the ciphertext is K. So perhaps the letters were shifted by 6 since this would then map E to K. Shifting the entire message by −6 gives us “THE EARLY BIRD GETS THE WORM.”

## Block Ciphers

- Ciphers that replace each letter of the alphabet by another letter are called *character* or *monoalphabetic* ciphers.
- They are vulnerable to cryptanalysis based on letter frequency. *Block ciphers* avoid this problem, by replacing blocks of letters with other blocks of letters.
- A simple type of block cipher is called the *transposition cipher*. The key is a permutation σ of the set {1,2,...,m}, where m is an integer, that is a one-to-one function from {1,2,...,m} to itself.
- To encrypt a message, split the letters into blocks of size m, adding additional letters to fill out the final block. We encrypt p₁,p₂,...,pₘ as c₁,c₂,...,cₘ = pσ(1),pσ(2),...,pσ(m).
- To decrypt the c₁,c₂,...,cₘ transpose the letters using the inverse permutation σ⁻¹.

## Block Ciphers

**Example:** Using the transposition cipher based on the permutation σ of the set {1,2,3,4} with σ(1) = 3, σ(2) = 1, σ(3) = 4, σ(4) = 2,

- a. Encrypt the plaintext PIRATE ATTACK
- b. Decrypt the ciphertext message SWUE TRAEOEHS, which was encrypted using the same cipher.

**Solution:**

- a. Split into four blocks PIRA TEAT TACK.
  Apply the permutation σ giving IAPR ETTA AKTC.
- b. σ⁻¹: σ⁻¹(1) = 2, σ⁻¹(2) = 4, σ⁻¹(3) = 1, σ⁻¹(4) = 3.
  Apply the permutation σ⁻¹ giving USEW ATER HOSE.
  Split into words to obtain USE WATER HOSE.

## Cryptosystems

**Definition:** A *cryptosystem* is a five-tuple $(\mathcal{P},\mathcal{C},\mathcal{K},\mathcal{E},\mathcal{D})$, where

- $\mathcal{P}$ is the set of plaintext strings.
- $\mathcal{C}$ is the set of ciphertext strings,
- $\mathcal{K}$ is the *keyspace* (set of all possible keys),
- $\mathcal{E}$ is the set of encryption functions, and
- $\mathcal{D}$ is the set of decryption functions.

The encryption function in $\mathcal{E}$ corresponding to the key $k$ is denoted by $E_k$ and the decryption function in $\mathcal{D}$ that decrypts cipher text encrypted using $E_k$ is denoted by $D_k$. Therefore:

$$D_k(E_k(p)) = p, \text{ for all plaintext strings } p.$$

## Cryptosystems

**Example:** Describe the family of shift ciphers as a cryptosystem.

**Solution:** Assume the messages are strings consisting of elements in Z₂₆.

- $\mathcal{P}$ is the set of strings of elements in Z₂₆,
- $\mathcal{C}$ is the set of strings of elements in Z₂₆,
- $\mathcal{K}$ = Z₂₆,
- $\mathcal{E}$ consists of functions of the form Eₖ(p) = (p + k) mod 26 , and
- $\mathcal{D}$ is the same as $\mathcal{E}$ where Dₖ(p) = (p − k) mod 26 .

