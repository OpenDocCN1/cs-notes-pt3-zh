# Figure 8.03

| ID | name | street | city | salary |
|---|---|---|---|---|
| ... |  |  |  |  |
| 57766 | Kim | Main | Perryridge | 75000 |
| 98776 | Kim | North | Hampton | 67000 |
| ... |  |  |  |  |

employee

| ID | name |
|---|---|
| ... |  |
| 57766 | Kim |
| 98776 | Kim |
| ... |  |

| name | street | city | salary |
|---|---|---|---|
| ... |  |  |  |
| Kim | Main | Perryridge | 75000 |
| Kim | North | Hampton | 67000 |
| ... |  |  |  |

natural join

| ID | name | street | city | salary |
|---|---|---|---|---|
| ... |  |  |  |  |
| 57766 | Kim | Main | Perryridge | 75000 |
| 57766 | Kim | North | Hampton | 67000 |
| 98776 | Kim | Main | Perryridge | 75000 |
| 98776 | Kim | North | Hampton | 67000 |
| ... |  |  |  |  |