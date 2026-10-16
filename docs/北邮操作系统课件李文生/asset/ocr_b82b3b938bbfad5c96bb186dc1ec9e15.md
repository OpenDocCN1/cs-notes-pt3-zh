# Network Devices

+   - Varying enough from block and character to have own interface
+   - Unix and Windows NT/9i/2000 include socket interface
+     - Separates network protocol from network operation
+     - The system calls in the socket interface enable an application
+       - To create a socket
+       - To connect a local socket to a remote address
+       - To listen for any remote application to plug into the local socket
+       - To send and receive packets over the connection
+     - Includes select functionality: manages a set of sockets
+   - Approaches vary widely (pipes, FIFOs, streams, queues, mailboxes)