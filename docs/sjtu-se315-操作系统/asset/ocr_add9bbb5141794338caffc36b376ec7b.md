# Recovery approach

+   1. Synchronous meta-data update + fsck
+      Used in xv6-rev0
+      During check, synchronize meta-data, such as file size
+   2. Soft update (FreeBSD fs modified on FFS)
+      Soft update, not covered in this course
+   3. Logging (ext 3/4), xv6-rev6 and following versions
+      Before doing actual meta-data update, log the event
+      After crash, recover from log