# # CAN Improvements

+   - CAN provides tradeoff between per-node state, *O(d)*, and path length, *O(dn<sup>1/d</sup>)*
+     - Path length is measured in application level hops
+     - Neighbor nodes may be geographically distant
+   - Want to achieve a lookup latency that is comparable to underlying IP path latency
+     - Several optimizations to reduce lookup latency also improve robustness in terms of routing and data availability
+   - Approach: reduce the path length, reduce the per-hop latency, and add load balancing
+   - Simulated CAN design on Transit-Stub (TS) topologies using the GT-ITM topology generator (Zegura, et. al.)