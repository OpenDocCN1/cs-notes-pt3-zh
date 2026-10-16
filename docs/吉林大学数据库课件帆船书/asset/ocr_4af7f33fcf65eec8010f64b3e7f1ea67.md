# Snapshot Isolation

+   - Motivation: Decision support queries that read large amounts of data have concurrency conflicts with OLTP transactions that update a few rows
+     - Poor performance results
+   - Solution 1: Give logical “snapshot” of database state to read only transactions, read-write transactions use normal locking
+     - Multiversion 2-phase locking
+     - Works well, but how does system know a transaction is read only?
+   - Solution 2: Give snapshot of database state to every transaction, updates alone use 2-phase locking to guard against concurrent updates
+     - Problem: variety of anomalies such as lost update can result
+     - Partial solution: snapshot isolation level (next slide)
+       - Proposed by Berenson et al, SIGMOD 1995
+       - Variants implemented in many database systems
+         - E.g. Oracle, PostgreSQL, SQL Server 2005