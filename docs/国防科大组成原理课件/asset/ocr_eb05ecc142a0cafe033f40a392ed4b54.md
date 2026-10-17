# MIPS定义的例外

| 例外号 | 名称 | 说明 |
|---|---|---|
| 0x00 | Int | 中断 |
| - | TLBRefill | TLB中找不到映射项，专用例外入口 |
| 0x01 | Mod | TLB中找到映射项，但其中D位为0 |
| 0x02, 0x03 | TLBL/S | TLB中找到映射项，但其中V位为0 |
| 0x04, 0x05 | AdEL/AdES | 非对齐、无权访问、非法64位 |
| 0x06, 0x07 | IBE/DBE | 总线错 |
| 0x08 | Sys | 系统调用 |
| 0x09 | Bp | 指令断点 (BREAK、SDBBP) |
| 0x0A | RI | 保留指令 |
| 0x0B | CpU | 协处理器不可用 |
| 0x0C | Ov | 整数溢出 |
| 0x0F | FPE | 浮点例外 |
| 0x17 | WATCH | 地址监视例外 |
| 0x18 | MCheck | 内部一致性问题，如TLB中一个VPN有多项映射 |
| 0x30 | CacheErr | Cache数据校验错 |