# Randomness

+   - So $M$ can output short descriptions of strings that fail to have property $f$ as follows:
+   - For any string $x$ that fail to have property $f$, let $i_x$ be the position (index) of $x$ on a list of all such strings. Suppose these strings are in length and lexicographically order. The length of the description of $x \langle M,i_x\rangle$ is $|i_x|+c$.
+   - Fix any number $b>0$, select $n$ such that at most a $1/2^{b+c+1}$ fraction of strings of length $n$ or less fail to have property $f$.