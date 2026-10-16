# LDAP URLs

+   - First part of URL specifis server and DN of base
+     - ldap://aura.research.bell-labs.com/o=Lucent,c=USA
+   - Optional further parts separated by ? symbol
+     - ldap://aura.research.bell-labs.com/o=Lucent,c=USA??sub?cn=Korth
+     - Optional parts specify
+       1. attributes to return (empty means all)
+       2. Scope (sub indicates entire subtree)
+       3. Search condition (cn=Korth)