# Sequential File Organization (Cont.)

+   - Deletion – use pointer chains
+   - Insertion – locate the position where the record is to be inserted
+     - if there is free space insert there
+     - if no free space, insert the record in an overflow block
+     - In either case, pointer chain must be updated
+   - Need to reorganize the file from time to time to restore sequential order

![](bbox=[0.43, 0.45, 0.95, 0.95])