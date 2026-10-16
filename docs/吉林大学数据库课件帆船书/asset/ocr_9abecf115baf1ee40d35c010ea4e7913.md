# Interquery Parallelism

+   - Queries/transactions execute in parallel with one another.
+   - Increases transaction throughput; used primarily to scale up a transaction processing system to support a larger number of transactions per second.
+   - Easiest form of parallelism to support, particularly in a shared-memory parallel database, because even sequential database systems support concurrent processing.
+   - More complicated to implement on shared-disk or shared-nothing architectures
+     - Locking and logging must be coordinated by passing messages between processors.
+     - Data in a local buffer may have been updated at another processor.
+     - **Cache-coherency** has to be maintained — reads and writes of data in buffer must find latest version of data.