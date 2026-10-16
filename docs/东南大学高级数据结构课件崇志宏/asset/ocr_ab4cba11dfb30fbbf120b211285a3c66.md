# System Model

+   - The application interacts with Chord in two main ways:
+     - Chord provides a lookup(key) algorithm that yields the IP address of the node responsible for the key.
+     - The Chord software on each node notifies the application of changes in the set of keys that the node is responsible for.