# Block Ciphers

+   - Ciphers that replace each letter of the alphabet by another letter are called *character* or *monoalphabetic* ciphers.
+   - They are vulnerable to cryptanalysis based on letter frequency. *Block ciphers* avoid this problem, by replacing blocks of letters with other blocks of letters.
+   - A simple type of block cipher is called the *transposition cipher*. The key is a permutation σ of the set {1,2,...,m}, where m is an integer, that is a one-to-one function from {1,2,...,m} to itself.
+   - To encrypt a message, split the letters into blocks of size m, adding additional letters to fill out the final block. We encrypt p₁,p₂,...,pₘ as c₁,c₂,...,cₘ = pσ(1),pσ(2),...,pσ(m).
+   - To decrypt the c₁,c₂,...,cₘ transpose the letters using the inverse permutation σ⁻¹.