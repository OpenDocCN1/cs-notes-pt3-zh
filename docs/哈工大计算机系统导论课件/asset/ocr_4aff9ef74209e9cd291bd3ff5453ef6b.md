# TLBs --- Making Address Translation Fast

问题：一次存储器引用要访问几次主存？ 0 / 1 / 2 / 3次？

把经常要查的页表项放到Cache中，这种在Cache中的页表项组成的页表称为 *Translation Lookaside Buffer* or *TLB*（快表）

TLB中的页表项：tag+主存页表项

| Virtual Address (tag) | Physical Address | Dirty | Ref | Valid | Access |
| --- | --- | --- | --- | --- | --- |
|  | 对应物理页框号 |  |  |  |  |

CPU访存时，地址中虚页号被分成tag+index，tag用于和TLB页表项中的tag比较，index用于定位需要比较的表项

TLB全相联时，没有index，只有Tag，虚页号需与每个Tag比较；TLB组相联时，则虚页号高位为Tag，低位为index，用作组索引。