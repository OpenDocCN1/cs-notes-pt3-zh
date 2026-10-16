# LR(0)分析表的构造算法

算法5.6 LR(0)分析表的构造。

输入： 文法G=(V, T, P, S)的拓广文法G'；

输出： G'的LR(0)分析表，即action表和goto表；

步骤：

+   1. 令I₀ = CLOSURE({S' →·S})，构造G'的LR(0)项目集规范族C={I₀,I₁,...,Iₙ}

+   2. 让Iᵢ对应状态i，I₀对应状态0，0为初始状态。

+   3. for k=0 to n do begin
+   (1) if A→α·aβ∈Iₖ & a∈T & GO(Iₖ, a)=Iⱼ then action[k,a]:=Sj;
+   (2) if A→α·Bβ∈Iₖ & B∈V & GO(Iₖ, B)=Iⱼ then goto[k,B]:=j;
+   (3) if A→α·∈Iₖ & A→α为G的第j个产生式then
+   for ∀a∈T∪{#} do action[k,a]:=rj;
+   (4) if S'→S·∈Iₖ then action[k,#]:=acc end;

+   4. 上述(1)到(4)步未填入信息的表项均置为error。