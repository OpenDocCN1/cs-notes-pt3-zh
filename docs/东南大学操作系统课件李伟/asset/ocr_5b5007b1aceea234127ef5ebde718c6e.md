# NFS Path-Name Translation

+   - Performed by breaking the path into component names and performing a separate NFS lookup call for every pair of component name and directory vnode
+   - To make lookup faster, a directory name lookup cache on the client’s side holds the vnodes for remote directory names