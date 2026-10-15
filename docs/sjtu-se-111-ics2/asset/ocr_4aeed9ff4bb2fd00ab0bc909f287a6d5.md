# Echo server: open_listenfd() (initialize)

+   - IP addr and port stored in network (big-endian) byte order
+     - `htonl()` converts longs from host byte order to network byte order.
+     - `htons()` convers shorts from host byte order to network byte order.