# Quiz #1

In IA32 architecture, when the CR4_PSE bit in %cr4 register is set, then superpage mode is enabled, and the operating system can use either 4KB sized page or 4MB sized page. There are tradeoffs between small page and large page.
Consider the following scenarios:

a) Dump the content of a large file of several hundred megabytes mapped to the RAM by mmap() function to another location:

```
memcpy(addr_of_new_location, addr_of_mapped_file, sizeof_file);
```

b) Do the following calculation, where A, B are int pointers:

```
for(i=0; i<0x40000; ++i){
    A[i] += B[i] & 0x3FFFFF;
}
```

Which sized (4KB or 4MB) page performs better in each scenario? Give your reasons.