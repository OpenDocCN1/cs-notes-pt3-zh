
## Immediate Database Modification Example

| Log | Write | Output |
|---|---|---|
| `<T_0 start>`<br>`<T_0, A, 1000, 950>`<br>`<T_0, B, 2000, 2050>`<br><br>`<T_0 commit>`<br>`<T_1 start>`<br>`<T_1, C, 700, 600>`<br><br>`<T_1 commit>` | `A = 950`<br>`B = 2050`<br><br>`C = 600` | `B_B, B_C`<br><br>`B_A` |

> > 🟥 Note: *B*<sub>X</sub> denotes block containing X.

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_828_0.png)

## Concurrency Control and Recovery

- With concurrent transactions, all transactions share a single disk buffer and a single log
  - A buffer block can have data items updated by one or more transactions
- We assume that *if a transaction Tᵢ has modified an item, no other transaction can modify the same item until Tᵢ has committed or aborted*
  - i.e. the updates of uncommitted transactions should not be visible to other transactions
    - Otherwise how to perform undo if T1 updates A, then T2 updates A and commits, and finally T1 has to abort?
  - Can be ensured by obtaining exclusive locks on updated items and holding the locks till end of transaction (strict two-phase locking)
- Log records of different transactions may be interspersed in the log.

## Undo and Redo on Recovering from Failure

- When recovering after failure:
  - Transaction $T_i$ needs to be undone if the log
    - contains the record <$T_i$ start>,
    - but does not contain either the record <$T_i$ commit> or <$T_i$ abort>.
  - Transaction $T_i$ needs to be redone if the log
    - contains the records <$T_i$ start>
    - and contains the record <$T_i$ commit> or <$T_i$ abort>

- Note that If transaction $T_i$ was undone earlier and the <$T_i$ abort> record written to the log, and then a failure occurs, on recovery from failure $T_i$ is redone
  - such a redo redooes all the original actions including the steps that restored old values
    - Known as repeating history
    - Seems wasteful, but simplifies recovery greatly

## Immediate DB Modification Recovery Example

Below we show the log as it appears at three instances of time.

```
<T₀ start>
<T₀, A, 1000, 950>
<T₀, B, 2000, 2050>
(a)
```

```
<T₀ start>
<T₀, A, 1000, 950>
<T₀, B, 2000, 2050>
<T₀ commit>
<T₁ start>
<T₁, C, 700, 600>
(b)
```

```
<T₀ start>
<T₀, A, 1000, 950>
<T₀, B, 2000, 2050>
<T₀ commit>
<T₁ start>
<T₁, C, 700, 600>
<T₁ commit>
(c)
```

Recovery actions in each case above are:

- (a) undo (T₀): B is restored to 2000 and A to 1000, and log records <T₀, B, 2000>, <T₀, A, 1000>, <T₀, abort> are written out
- (b) redo (T₀) and undo (T₁): A and B are set to 950 and 2050 and C is restored to 700. Log records <T₁, C, 700>, <T₁, abort> are written out.
- (c) redo (T₀) and redo (T₁): A and B are set to 950 and 2050 respectively. Then C is set to 600

## Checkpoints

- Redoing/undoing all transactions recorded in the log can be very slow
  1. processing the entire log is time-consuming if the system has run for a long time
  2. we might unnecessarily redo transactions which have already output their updates to the database.
- Streamline recovery procedure by periodically performing checkpointing
  1. Output all log records currently residing in main memory onto stable storage.
  2. Output all modified buffer blocks to the disk.
  3. Write a log record < checkpoint L> onto stable storage where L is a list of all transactions active at the time of checkpoint.
  - All updates are stopped while doing checkpointing

## Checkpoints (Cont.)

During recovery we need to consider only the most recent transaction T_i that started before the checkpoint, and transactions that started after T_i.

1. Scan backwards from end of log to find the most recent <checkpoint> record

• Only transactions that are in L or started after the checkpoint need to be redone or undone

• Transactions that committed or aborted before the checkpoint already have all their updates output to stable storage.

Some earlier part of the log may be needed for undo operations

1. Continue scanning backwards till a record <T_i start> is found for every transaction T_i in L.

• Parts of log prior to earliest <T_i start> record above are not needed for recovery, and can be erased whenever desired.
