# Persistent Java Systems

+   - Standard for adding persistence to Java : Java Database Objects (JDO)
+     - Persistence by reachability
+     - Byte code enhancement
+       - Classes separately declared as persistent
+       - Byte code modifier program modifies class byte code to support persistence
+         - E.g. Fetch object on demand
+         - Mark modified objects to be written back to database
+     - Database mapping
+       - Allows objects to be stored in a relational database
+     - Class extents
+     - Single reference type
+       - no difference between in-memory pointer and persistent pointer
+       - Implementation technique based on hollow objects (a.k.a. pointer swizzling)

![](bbox=[0.0, 0.05, 0.12, 0.15])