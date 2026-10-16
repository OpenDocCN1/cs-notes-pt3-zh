

## 数据流方程求解过程中的3个关键因素

- 当前语句产生和注销的信息取决于需要解决的具体问题：可以由 in[S] 定义 out[S]，也可以反向定义，由 out[S] 定义 in[S]
- 由于数据是沿着程序的执行路径，也就是控制流路径流动，因此数据流分析的结果受到程序控制结构的影响
- 代码中出现的诸如过程调用、指针访问以及数组成员访问等操作，对定义和求解一个数据流方程都会带来不同程度的困难

## 基本块B的到达定义数据流方程

- out[B] = gen[B] ∪ ( in[B] − kill[B] )
  - in[B]为进入基本块时的数据流信息
  - kill[B] = kill[d1] ∪ kill[d2] ... ∪ kill[dn]，d1~dn依次为基本块中的语句
  - gen[B] = gen[dn] ∪ (gen[d(n-1)] − kill[dn]) ∪ (gen[d(n-2)] − kill[d(n-1)] − kill[dn]) ... ∪ (gen[d1] - kill[d2] − kill[d3] ... - kill[dn])

## 例：

- out[B] = gen[B] ∪ ( in[B] − kill[B] )
- in[B]为进入基本块时的数据流信息
- kill[B] = kill[d1] ∪ kill[d2] ... ∪ kill[dn]，d1~dn依次为基本块中的语句
- gen[B] = gen[dn] ∪ (gen[d(n-1)] − kill[dn]) ∪ (gen[d(n-2)] − kill[d(n-1)] − ... − kill[dn]) ... ∪ (gen[d1] - kill[d2] - kill[d3] ... - kill[dn])

d1: a = b + 1

d2: a = b + 2

kill[B] = kill[d1] ∪ kill[d2] = {d2} ∪ {d1} = {d1, d2}

gen[B] = gen[d2] ∪ (gen[d1] − kill[d2]) = {d2} ∪ ({d1} − {d1}) = {d2}

out[B] = gen[B] ∪ ( in[B] − kill[B] ) = {d2} ∪ (in[B] − {d1, d2})

```text
入口

B1
d1: x = a
d2: y = b
d3: i = 0

B2
cmp i, 100

B3
d4: z = a * 10
d5: x = x + y
cmp x, z

B4
d6: x = x - y

B5
d7: y = y + 1
d8: i = i + 1

B_exit
出口

gen[B1] = {d1, d2, d3}
kill[B1] = {d5, d6, d7, d8}

gen[B2] = {}
kill[B2] = {}

gen[B3] = {d4, d5}
kill[B3] = {d1, d6}

gen[B4] = {d6}
kill[B4] = {d1, d5}

gen[B5] = {d7, d8}
kill[B5] = {d2, d3}
```

## 算法13.3 基本块的到达定义数据流分析

- 输入：程序流图，且基本块的kill集合和gen集合已经计算完毕
- 输出：每个基本块入口和出口处的in和out集合，即in[B]和out[B]
- 方法：
  1. 将包括代表流图出口基本块B_exit在内的所有基本块的out集合，初始化为空集。
  2. 根据方程in[B] = ∪_{B的前驱基本块P} out[P]，out[B] = gen[B] ∪ ( in[B] − kill[B] )，为每个基本块B依次计算集合in[B]和out[B]。如果某个基本块计算得到的out[B]与该基本块此前计算得出的out[B]不同，则循环执行步骤2，直到所有基本块的out[B]集合不再产生变化为止。

## 例：到达定义数据流分析

in[B] = ∪_{B的前驱基本块P} out[P]
out[B] = gen[B] ∪ ( in[B] − kill[B] )

```text
B1
d1: x = a
d2: y = b
d3: i = 0

B2
cmp i, 100

B3
d4: z = a * 10
d5: x = x + y
cmp x, z

B4
d6: x = x - y

B5
d7: y = y + 1
d8: i = i + 1

B_exit 出口
```

in[B1] = {}, out[B1] = {d1, d2, d3}
in[B2] = {d1, d2, d3, d4, d5, d6, d7, d8}, out[B2] = {d1, d2, d3, d4, d5, d6, d7, d8}
in[B3] = {d1, d2, d3, d4, d5, d6, d7, d8}, out[B3] = {d2, d3, d4, d5, d7, d8}
in[B4] = {d2, d3, d4, d5, d7, d8}, out[B4] = {d2, d3, d4, d6, d7, d8}
in[B5] = {d2, d3, d4, d5, d6, d7, d8}, out[B5] = {d4, d5, d6, d7, d8}
in[B_exit] = {d1, d2, d3, d4, d5, d6, d7, d8}

## 13.2.2 活跃变量分析

- 变量x在某个执行点p是活跃的
  - 在流图中沿着从p开始的某条路径中可能引用变量x在p点的值
- 数据流方程如下：
  - in[B] = use[B] ∪ (out[B] − def[B])
  - out[B] = ∪_{B的后继基本块P} in[P]
  - def[B]：变量在B中被定义（赋值）先于任何对它们的使用
  - use[B]：变量在B中被使用先于任何对它们的定义

## 与到达定义分析的区别

活跃变量分析：
in[B] = use[B] ∪ (out[B] − def[B])

到达定义分析：
out[B] = gen[B] ∪ ( in[B] − kill[B] )

- 采用use[B]代表当前基本块新生成的数据流信息
- 采用def[B]代表当前基本块消除的数据流信息
- 采用in[B]而不是out[B]来计算当前基本块中的数据流信息
- 采用out[B]而不是in[B]来计算其它基本块汇集到当前基本块的数据流信息
- 在汇集数据流信息时，考虑的是后继基本块而不是前驱基本块

## def和use

- def[B]指的是在基本块B中，在使用前被定义的变量集合
  - 在引用该变量前已经对该变量进行了赋值
- use[B]指的是在基本块B中，在定义前被使用的变量集合
  - 在该变量的任何定义之前对其引用

## 例

| 流图 | def[B] | use[B] |
| --- | --- | --- |
| 入口 |  |  |
| B1<br>d1: x = a<br>d2: y = b<br>d3: i = 0 | x, y, i | a, b |
| B2<br>cmp i, 100 | ∅ | i |
| B3<br>d4: z = a * 10<br>d5: x = x + y<br>cmp x, z | z | a, x, y |
| B4<br>d6: x = x - y | ∅ | x, y |
| B5<br>d7: y = y + 1<br>d8: i = i + 1 | ∅ | y, i |
| B_exit<br>出口 |  |  |

## 算法13.4 基本块的活跃变量数据流分析

- 输入：程序流图，且基本块的use集合和def集合已经计算完毕
- 输出：每个基本块入口和出口处的in和out集合，即in[B]和out[B]
- 方法：
  1. 将包括代表流图出口基本块B_exit在内的所有基本块的in集合，初始化为空集。
  2. 根据方程out[B] = ∪_{B的后继基本块P} in[P]，in[B] = use[B] ∪ (out[B] − def[B])，为每个基本块B依次计算集合out[B]和in[B]。如果计算得到某个基本块的in[B]与此前计算得出的该基本块in[B]不同，则循环执行步骤2，直到所有基本块的in[B]集合不再产生变化为止。

```text
for 每个基本块B do in[B] = ∅ ;
while 集合in发生变化 do
    for 每个基本块B do begin
        out[B] = ∪_{B的所有后继S} in[S]
        in[B] = use[B] ∪ (out[B] − def[B])
    end
```

