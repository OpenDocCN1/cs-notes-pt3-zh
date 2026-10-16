# Concurrency Control

+   - Correctness without serializability:
+     - Correctness depends on the specific consistency constraints for the databases.
+     - Correctness depends on the properties of operations performed by each transaction.
+   - Use database consistency constraints as to split the database into subdatabases on which concurrency can be managed separately.
+   - Treat some operations besides read and write as fundamental low-level operations and extend concurrency control to deal with them.