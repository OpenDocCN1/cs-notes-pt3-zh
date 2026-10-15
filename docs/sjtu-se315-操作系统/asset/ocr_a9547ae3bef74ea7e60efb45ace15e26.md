```
17 int
18 main(void)
19 {
20   kinit1(end, P2V(4*1024*1024)); // phys page allocator
21   kvmalloc();        // kernel page table
22   mpinit();          // collect info about this machine
```

```
146 // Allocate one page table for the machine for the kernel address
147 // space for scheduler processes.
148 void
149 kvmalloc(void)
150 {
151   kpgdir = setupkvm();
152   switchkvm();
153 }
```

```
155 // Switch h/w page table register to the kernel-only page table,
156 // for when no process is running.
157 void
158 switchkvm(void)
159 {
160   lcr3(v2p(kpgdir));   // switch to the kernel page table
161 }
```