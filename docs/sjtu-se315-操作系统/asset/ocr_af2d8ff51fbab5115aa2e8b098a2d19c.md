# Introduction to google file system

+   - Shares same goals as previous distributed file systems, but with some differences.
+     - Component failures are considered the norm rather than the exception.
+     - Files are huge by traditional standards.
+     - Most files are mutated by appending new data rather than overwriting existing data.
+     - Co-designing the file system and applications increases flexibility in development.