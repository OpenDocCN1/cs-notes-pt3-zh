# Replication with Weak Consistency

+   - Many systems support replication of data with weak degrees of consistency (i.e., without a guarantee of serializability)
+     - i.e. Q_R + Q_W <= S or 2*Q_W < S
+     - Usually only when not enough sites are available to ensure quorum
+       - But sometimes to allow fast local reads
+     - Tradeoff of consistency versus availability or latency
+   - Key issues:
+     - Reads may get old versions
+     - Writes may occur in parallel, leading to inconsistent versions
+       - Question: how to detect, and how to resolve
+         - Version vector scheme, Section 25.5.4