# message passing facility in Windows XP-- LPC

+   - LPC Communicates between two processes on the same machine.
+   - a port object is used to establish and maintain a connection between two processes.
+   - two types of ports:
+     - Connection ports
+       named objects, visible to all processes;
+       used to set up communication channels.
+     - Communication ports
+   - Communication works
+     - Client opens a handle to the subsystem’s connection port object
+     - Client sends a connection request
+     - Server creates two private communication ports and returns the handle to one of them to the client
+     - Client and server use the corresponding port handle to send messages or callbacks and to listen for replies