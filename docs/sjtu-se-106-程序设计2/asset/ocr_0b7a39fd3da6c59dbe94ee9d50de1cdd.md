# Size of a Message Digest / Hash Value

+   - h : {0,1}* → {0,1}^n
+     - If n = 64, the probability of finding one collision will be higher than half after slightly more than 2^32 random hashes being tried.
+     - If there exists a machine which can carry out 100,000 hashes per second, it takes 12 hours for finding the first collision with probability higher than half.

+   - Recommended message digest lengths (in bits): 128 (MD5), 160 (SHA-1), 256 (SHA-256) or 512 (SHA-512)

+   - For those recommended lengths, because the number of possible hashes is so large, the odds of finding one by chance is negligibly small (one in 2^80 for SHA-1).