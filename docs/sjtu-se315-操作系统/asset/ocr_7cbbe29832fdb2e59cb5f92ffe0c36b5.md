# VT-x extension: Extended Page Table (EPT)

![](bbox=[0.121, 0.272, 0.878, 0.638])

All guest-physical addresses go through extended page tables

Includes address in CR3, address in PDE, address in PTE, etc.

Reduces the frequency of VM exits to VMM.

The net effect of both implementations (EPT or NPT) is to allow the guest OS to own and manage its own page table, and not force the host to get involved.