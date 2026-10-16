# Indirect Communication(1/3)

+   - Messages are sent and received from mailboxes (also referred to as ports).
+     - Each mailbox has a unique id.
+     - Processes can communicate only if they share a mailbox.
+   - Primitives are defined as:
+     - send(A, message) – send a message to mailbox A
+     - receive(A, message) – receive a message from mailbox A
+   - Properties of communication link
+     - Link established only if processes share a common mailbox
+     - A link may be associated with many processes.
+     - Each pair of processes may share several communication links.
+     - Link may be unidirectional or bi-directional.