# Translating with the P6 page tables (case 0/1)

![](bbox=[0.15, 0.24, 0.68, 0.97])

Mem

Disk

+   - Case 0/1: page table missing but page present.

+   - Introduces consistency issue.

+   - potentially every page out requires update of disk page table.

+   - Linux disallows this

+   - if a page table is swapped out, then swap out its data pages too.