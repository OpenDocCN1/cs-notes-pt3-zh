# 8.5.1 UDP报头

+   - UDP数据包的长度 (Length)： UDP长度字段指的是UDP首部和UDP数据的字节长度。UDP数据报长度是IP全长减去IP首部的长度。最小值是8。

+   - UDP检验和 (Checksum)： 检验和字段用来检验传输过程中是否出现了错误。UDP检验和覆盖UDP首部、伪首部和UDP数据。