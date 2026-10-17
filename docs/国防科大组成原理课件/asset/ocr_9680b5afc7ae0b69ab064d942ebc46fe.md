# MIPS32存储空间分段情况

| 地址范围 | 容量 | 映射方式 | Cached | 访问权限 |
|---|---|---|---|---|
| 0xe0000000–0xffffffff | 0.5GB | 查找TLB | Yes (TLB) | Kernel |
| 0xc0000000–0xdfffffff | 0.5GB | 查找TLB | Yes (TLB) | Kernel, Supervisor |
| 0xa0000000–0xbfffffff | 0.5GB | 地址-0xa0000000 | No | Kernel |
| 0x80000000–0x9fffffff | 0.5GB | 地址-0x80000000 | Yes (Config) | Kernel |
| 0x00000000–0x7fffffff | 2GB | 查找TLB | Yes (TLB) | Kernel, Supervisor, User |