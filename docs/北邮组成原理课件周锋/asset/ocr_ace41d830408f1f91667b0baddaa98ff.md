# 流水线的实现

存储器访问/分支完成周期（MEM）

+   所有指令都要在该周期对PC进行更新。
+   除了分支指令，其他指令都是做PC←NPC

+   在该周期内处理的指令仅仅有load、store和分支三种指令。

+   存储器访问指令
+   LMD←Mem[ALUo] 或者 Mem[ALUo]←B

+   分支指令
+   if (cond) PC ←ALUo else PC←NPC