# Detecting Inconsistent Updates

+   - Version vector scheme used to detect inconsistent updates to documents at different hosts (sites).

+   - Copies of document *d* at hosts *i* and *j* are **inconsistent** if:
+     1. the copy of document *d* at *j* contains updates performed by host *k* that have not been propagated to host *j* (*k* may be the same as *j*), and
+     2. the copy of *d* at *j* contains updates performed by host *l* that have not been propagated to host *i* (*l* may be the same as *j*).

+   - Basic idea: each host *i* stores, with its copy of each document *d*, a **version vector** - a set of version numbers, with an element \(V_{d,i}[k]\) for every other host *k*.

+   - When a host *j* updates a document *d*, it increments the version number \(V_{d,j}[j]\) by 1.