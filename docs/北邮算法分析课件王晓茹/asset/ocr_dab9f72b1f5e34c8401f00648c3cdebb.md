```
bestx[1:n]：记录最佳路径；cw: 当前部分路径的总长

BacktrackTSP(i)
1. if i=n then  //已经搜索到叶节点，已经选择了最后1个城市
{
2.     if w(x[n-1], x[n]) ≠∞ and w(x[n],1 ) ≠∞
        // 最后1个城市与前一城市相连、与第1个城市相连，
        // 组成1个满足条件的回路
3.     then //比较当前回路与以前最佳回路，看当前回路
        是否更优
4.     if cw + w(x[n-1], x[n]) + w(x[n],1 ) < bestw
5.         then {  //当前回路更优，更新最优搜索结果
6.         bestw = cw + w(x[n-1], x[n]) + w(x[n],1 ) ;
7.         for j=1 to n do bestx[j]=x[j]
}
```