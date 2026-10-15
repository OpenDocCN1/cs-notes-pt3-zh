# big picture of xv6's virtual addressing scheme

0x00000000:0x80000000
user addresses below KERNBASE

0x80000000:0x80100000
map low 1MB devices (for kernel)

0x80100000:?
kernel instructions/data

? :0x8E000000
224 MB of DRAM mapped here

0xFE000000:0x00000000
more memory-mapped devices