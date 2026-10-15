# RPC: Failure Handling

+   - 1. At least once
+     - Client keeps resending until server responds
+     - Only OK without side effects
+   - 2. At most once
+     - Client keeps resending (may time-out)
+     - Server remembers requests and suppress duplicates
+   - 3. Exactly once
+     - This is often what we really want
+     - Hard to do in a useful way, later in Chap-8 and 10
+   - Most RPC system do #1 or #2

Most network systems and applications also have these considerations