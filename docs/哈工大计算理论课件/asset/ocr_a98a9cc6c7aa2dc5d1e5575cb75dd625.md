# Undecidable problems from language theory

+   - $HALT_{TM} = \{\langle M, w\rangle \mid M \text{ is a TM and } M \text{ halts on input } w\}$
+     So $HALT_{TM}$ determine whether a Turing machine halts on a given input.

+   - Prove $HALT_{TM}$ is undecidable.
+     Proof:

+   - This proof is by contradiction. Assume that $HALT_{TM}$ is decidable. After showing that $A_{TM}$ is reducible to $HALT_{TM}$, we can conclude that $A_{TM}$ is decidable, so there is a contradiction.