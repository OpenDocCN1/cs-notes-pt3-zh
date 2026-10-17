# 主频 vs. 性能

| CPU型号 | 频率(GHz) | SPEC_Int | SPEC_Fp | 微体系结构 | 硬件时间 |
|---|---|---|---|---|---|
| Pentium4 670 | 3.80 | 11.5 | 12.2 | Netburst/P4 | 2005.05 |
| T7600 | 2.33 | 14.0 | 12.5 | Core/Core 2 Duo | 2006.09 |
| Xeon 5160 | 3.00 | 17.5 | 15.4 | Core/ Woodcrest | 2007.01 |
| Xeon X5482 | 3.20 | 25.3 | 21.2 | Core/Harpertown | 2007.11 |
| Core i7-965 EE | 3.20 | 32.1 | 38.5 | Nehalem/Desktop | 2008.11 |
| Xeon X5570 | 3.33 | 34.5 | 38.4 | Nelamen/Gainestown | 2009.03 |
| Xeon X5650 | 2.67 | 35.9 | 51.3 | Nehalem/Gulftown | 2010.04 |
| Core i3-2100 | 3.10 | 34.1 | 48.0 | Sandy Bridge/Desktop | 2011.05 |
| Xeon E3-1280 | 3.50 | 45.8 | 58.9 | Sandy Bridge | 2011.03 |
| Xeon E5-2690 | 2.90 | 55.4 | 89.6 | Sandy Bridge-EP | 2012.05 |

+   - 主频降低了，单核性能大幅度提高（SPECint/fp2006）
+     - 性能的提高少量来自于自动并行化，主要是浮点
+   - 主要通过结构优化提高性能
+     - 骨架变大了（马变成了骆驼）：多访存部件、向量化、大队列……
+     - 细节做精了（结合应用的具体优化）