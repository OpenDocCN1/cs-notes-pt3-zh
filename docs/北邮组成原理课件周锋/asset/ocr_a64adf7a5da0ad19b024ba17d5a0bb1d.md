# DRAM读时序

+   - DRAM的访问开始于：RAS_L的下降沿
+   - 有2种读方式：OE_L早于或晚于CAS信号有效

DRAM 读周期时间 tRC

tPC

Addr. /9 256K x 8 DRAM Data /8

RAS_L

CAS_L

A 行地址 列地址 Junk 行地址 列地址 Junk

WE_L

OE_L

D 高阻 Junk 读出数据 高阻 读出数据

读访问时间 tCAC tRAC

输出使能延迟

早读周期: OE_L 早于 CAS_L信号有效

晚读周期: OE_L 晚于CAS_L信号有效