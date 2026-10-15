# Indirect Communication

+   - Mailbox sharing
+     - *P*₁, *P*₂, and *P*₃ share mailbox A
+     - *P*₁, sends; *P*₂ and *P*₃ receive
+     - Who gets the message?
+   - Solutions
+     - Allow a link to be associated with at most two processes
+     - Allow only one process at a time to execute a receive operation
+     - Allow the system to select arbitrarily the receiver. Sender is notified who the receiver was.