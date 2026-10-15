# File Name Search in ExFAT

+   - Search name by hash value first
+     - Hash the upper case version of the file name
+     - Each record in the directory is searched by comparing the hash value
+     - When a match is found, the filenames are compared to ensure that the proper file was located in case of collisions
+       - Only two characters have to be compared, why?