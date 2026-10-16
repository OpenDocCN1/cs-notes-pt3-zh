# Access control (1/2)

+   - Mode of access: **read, write, execute**
+   - Access-control list (ACL): associates with each file and specifies the user name and the types of access allowed for each user.
+   - Three classes of users
+     - **Owner**: the user who created the file.
+     - **Group**: a set of users who are sharing the file and need similar access.
+     - **Universe (Public)**: all other users in the system.
+   - Access-control information
+     - User access: RWX (111 – 7)
+     - Group access: RW– (110 – 6)
+     - Public access: ––X (001 – 1)