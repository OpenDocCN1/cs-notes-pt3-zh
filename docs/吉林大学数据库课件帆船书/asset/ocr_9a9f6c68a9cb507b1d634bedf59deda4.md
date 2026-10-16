# View Serializability

Let S and S′ be two schedules with the same set of transactions. S and S′ are view equivalent if the following three conditions are met, for each data item Q,

+   1. If in schedule S, transaction T_i reads the initial value of Q, then in schedule S′ also transaction T_i must read the initial value of Q.
+   2. If in schedule S transaction T_i executes read(Q), and that value was produced by transaction T_j (if any), then in schedule S′ also transaction T_i must read the value of Q that was produced by the same write(Q) operation of transaction T_j.
+   3. The transaction (if any) that performs the final write(Q) operation in schedule S must also perform the final write(Q) operation in schedule S′.

As can be seen, view equivalence is also based purely on reads and writes alone.