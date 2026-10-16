# Secondary Indices Example

Secondary index on salary field of instructor

| 40000 |  |
| 60000 |  |
| 62000 |  |
| 65000 |  |
| 72000 |  |
| 75000 |  |
| 80000 |  |
| 87000 |  |
| 90000 |  |
| 92000 |  |
| 95000 |  |

| 10101 | Srinivasan | Comp. Sci. | 65000 |  |
| 12121 | Wu | Finance | 90000 |  |
| 15151 | Mozart | Music | 40000 |  |
| 22222 | Einstein | Physics | 95000 |  |
| 32343 | El Said | History | 60000 |  |
| 33456 | Gold | Physics | 87000 |  |
| 45565 | Katz | Comp. Sci. | 75000 |  |
| 58583 | Califieri | History | 62000 |  |
| 76543 | Singh | Finance | 80000 |  |
| 76766 | Crick | Biology | 72000 |  |
| 83821 | Brandt | Comp. Sci. | 92000 |  |
| 98345 | Kim | Elec. Eng. | 80000 |  |

+   - Index record points to a bucket that contains pointers to all the actual records with that particular search-key value.
+   - Secondary indices have to be dense

![](bbox=[0.18, 0.15, 0.92, 0.65])