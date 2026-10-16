# 4. IBM PC/XT 的控制核心

来自电源
PWR GOOD

DMA WAIT
RDY/WAIT
AEN1

来自DMA控制器
来自存储控制器

当DMAWAIT为高，RDY/WAIT为低时，Ready输出为高电平；反之，输出低电平。

U₇、U₅、U₆的存取受AENBRD的控制
在DMA操作期间，地址只能锁存，不能送至总线。

AENBRD
AEN

来自系统
AENBRD低，AEN高时，CPU控制总线，8288工作；反之，进行DMA操作。

系统地址总线

系统数据总线

系统控制总线

![](bbox=[0.1, 0.1, 0.98, 0.95])