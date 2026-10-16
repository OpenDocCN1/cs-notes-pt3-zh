![](bbox=[0.0, 0.0, 0.12, 0.15])

# Alternative Models (Cont.)

+   - Motivating example: funds transfer between two banks
+     - Two phase commit would have the potential to block updates on the accounts involved in funds transfer
+     - Alternative solution:
+       - Debit money from source account and send a message to other site
+       - Site receives message and credits destination account
+     - Messaging has long been used for distributed transactions (even before computers were invented!)
+   - Atomicity issue
+     - once transaction sending a message is committed, message must guaranteed to be delivered
+       - Guarantee as long as destination site is up and reachable, code to handle undeliverable messages must also be available
+         - e.g. credit money back to source account.
+     - If sending transaction aborts, message must not be sent