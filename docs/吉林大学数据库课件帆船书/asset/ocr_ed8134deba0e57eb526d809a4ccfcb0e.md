# Example of Recovery

older

# Beginning of log

<T0 start>
<T0, B, 2000, 2050>
<T1 start>
<checkpoint {T0, T1}>
<T1, C, 700, 600>
<T1 commit>
<T2 start>
<T2, A, 500, 400>
<T0, B, 2000>
<T0 abort>
<T2, A, 500>
<T2 abort>

newer

End of log at crash!

Log records added during recovery

T0 rollback (during normal operation) begins

T0 rollback complete

T2 is incomplete at crash

T2 rolled back in undo pass

# Redo Pass

Start log records found for all transactions in undo list

Undo list: T2

# Undo Pass