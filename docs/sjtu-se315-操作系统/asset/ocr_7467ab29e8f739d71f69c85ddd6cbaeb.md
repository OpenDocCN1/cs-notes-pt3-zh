# NTFS File Record Attributes

+   - File Attributes
+     - View each file and folder as a set of file attributes
+     - Resident Attributes vs. Nonresident Attributes
+       - Small files and folders are entirely contained within the file’s MFT record (*typically, less than 900 bytes*)
+     - Types:
+       - Standard Info: access mode, timestamp, link count …
+       - Attribute List: locations of all nonresident attributes
+       - File Name: long and short file names
+       - Data / Index: data of file or index of folder
+       - Object ID: volume-unique file identifier
+       - …