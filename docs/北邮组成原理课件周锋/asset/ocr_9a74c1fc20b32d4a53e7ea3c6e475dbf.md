# 双端口存储器实例

# 双端口存储器IDT7133

+   - 容量为2K×16位SRAM
+   - 两个相互独立的端口，即左端口和右端口
+   - 左、右端口分别具有各自的地址线、数据线和控制线
+   - 图中下标L表示左端口，R表示右端口，LB表示低位字节，UB表示高位字节

Pin Names 管脚说明

| Left Port | Right Port | Names |
|---|---|---|
| CEL | CER | Chip Enable |
| R/WLUB | R/WRUB | Upper Byte Read/Write Enable |
| R/WLLB | R/WRLB | Lower Byte Read/Write Enable |
| OEL | OER | Output Enable |
| A0L - A10L | A0R - A10R | Address |
| I/O0L - I/O15L | I/O0R - I/O15R | Data Input/Output |
| BUSYL | BUSYR | Busy Flag |
| Vcc |  | Power |
| GND |  | Ground |