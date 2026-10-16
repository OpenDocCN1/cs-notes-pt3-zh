# ENCRYPTION IN DATABASES

+   - Database widely support encryption
+   - Different levels of encryption:
+     - **disk block**
+       - every disk block encrypted using key available in database-system software.
+       - Even if attacker gets access to database data, decryption cannot be done without access to the key.
+     - **Entire relations, or specific attributes of relations**
+       - non-sensitive relations, or non-sensitive attributes of relations need not be encrypted
+       - however, attributes involved in primary/foreign key constraints cannot be encrypted.
+   - Storage of encryption or decryption keys
+     - typically, single master key used to protect multiple encryption/decryption keys stored in database
+   - Alternative: encryption/decryption is done in application, before sending values to the database