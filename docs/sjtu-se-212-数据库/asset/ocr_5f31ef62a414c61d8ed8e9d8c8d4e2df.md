# MVD

+   - inst_info(ID, child_name, phone_number)

| ID | Child_name | Phone_number |
|---|---|---|
| 99999 | David | 512-555-1234 |
| 99999 | David | 512-555-4321 |
| 99999 | William | 512-555-1234 |
| 99999 | William | 512-555-4321 |

+   - BCNF, why?
+   - 仍有冗余，仍有异常
+   - MVD
+     - ID →→ child_name
+     - ID →→ phone_number