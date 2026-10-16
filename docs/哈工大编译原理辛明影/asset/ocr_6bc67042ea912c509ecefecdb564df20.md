# LR分析器操作

+   1. If action[sₘ,aᵢ]= sⱼ then 格局变为
+   s₀s₁… sₘj #X₁…Xₘaᵢ    aᵢ₊₁…aₙ#
+   对应“句型” X₁…Xₘaᵢaᵢ₊₁…aₙ

+   2. If action[sₘ,aᵢ]= rᵢ then 表示用第i个产生式
+   A→Xₘ₋₍ₖ₋₁₎…Xₘ进行归约，格局变为：

①.归约前：

s₀s₁… sₘ₋ₖ Sₘ₋₍ₖ₋₁₎…Sₘ   #X₁…Xₘ₋ₖ Xₘ₋₍ₖ₋₁₎…Xₘ₋ₖ
    aᵢaᵢ₊₁…aₙ#