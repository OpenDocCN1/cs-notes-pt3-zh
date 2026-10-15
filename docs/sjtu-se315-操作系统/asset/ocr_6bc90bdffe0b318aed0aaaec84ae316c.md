# Summary of GFS

+   - Metadata fit in memory
+   - Flat namespace
+   - Dedicated Care for Component Failure
+     - hard disk failure, data corruption, network disconnection, etc.
+   - High-throughput
+     - Minimized the master involvement
+       - Chunk servers themselves send and receive the client data
+       - The master leases authority to mutate chunks