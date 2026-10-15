# Stateless on NFS server

+   - Stateless on NFS server
+     - Each RPC contains all the information
+   - What about file cursor?
+     - Client maintains the state, e.g. the file cursor
+   - Client can repeat a request until it receives a reply
+     - Server may execute the same request twice
+     - Solution: each RPC is tagged with a transaction number, and server maintains some "soft" state: reply cache
+     - What if the server fails between two same requests?