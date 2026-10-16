# Scalable key Location

+   - Let *m* be the number of bits in the key/node identifiers.
+   - Each node, *n*, maintains a routing table with (at most) *m* entries, called the *finger table*.
+   - The *i*th entry in the table at node *n* contains the identity of the *first* node, *s*, that succeeds *n* by at least 2^i -1 on the identity circle.