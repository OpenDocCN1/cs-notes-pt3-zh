# accept() illustrated

1. Server blocks in accept, waiting for connection request on listening descriptor listenfd.

2. Client makes connection request by calling and blocking in connect.

3. Server returns connfd from accept.
Client returns from connect.
Connection is now established between clientfd and connfd.

![](bbox=[0.04, 0.25, 0.55, 0.82])