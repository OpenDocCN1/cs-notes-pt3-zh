# Free Lists

+   - Store the address of the first deleted record in the file header.
+   - Use this first record to store the address of the second deleted record, and so on
+   - Can think of these stored addresses as pointers since they “point” to the location of a record.
+   - More space efficient representation: reuse space for normal attributes of free records to store pointers. (No pointers stored in in-use records.)

|  |  |  |  |
|---|---|---|---|
| 10101 | Srinivasan | Comp. Sci. | 65000 |
|  |  |  |  |
| 15151 | Mozart | Music | 40000 |
| 22222 | Einstein | Physics | 95000 |
|  |  |  |  |
| 33456 | Gold | Physics | 87000 |
|  |  |  |  |
| 58583 | Califeri | History | 62000 |
| 76543 | Singh | Finance | 80000 |
| 76766 | Crick | Biology | 72000 |
| 83821 | Brandt | Comp. Sci. | 92000 |
| 98345 | Kim | Elec. Eng. | 80000 |

![](bbox=[0.193, 0.496, 0.758, 0.969])