

## 递归排列生成器

```
procedure recursiveGenPerms(i,n)
    if i>n then begin {We’re done, print the answer.}
        for k := 1 to n print perm_k ; print newline
    end else
        for j := 1 to n {Consider all poss. next items.}
            if ¬used_j then begin {Choose item j.}
                used_j := T; perm_i := j
                recursiveGenPerms(i+1,n)
                used_j := F      {Now back up}
            end
```

## 按顺序生成下一个排列

- 给定 $\{1,\dots,n\}$ 的一个现有排列 $a_1,\dots,a_n$，我们如何找到*下一个*排列？
- 过程概要：
  - 找到最大的 $j$，使得 $a_j < a_{j+1}$。
  - 在 $a_{j+1},\dots,a_n$ 中找到大于 $a_j$ 的最小整数，并将其放在位置 $j$。
  - 将 $a_j,\dots,a_n$ 中剩余的整数按从小到大排序，并把它们放到位置 $j+1$ 到 $n$。

## 下一个排列算法

```
procedure nextPerm(a₁,...,aₙ: perm. {1,...,n})
  j:=n−1; while aⱼ>aⱼ₊₁ and j>0 do j:=j−1
  if j=0 then return {no more permutations}
  k:=n; while aⱼ > aₖ do k:=k−1
  swap(aⱼ, aₖ); r:=n; s:=j+1
  while r>s do begin
    swap(aᵣ,aₛ); r:=r−1; s:=s+1 end
```

## 组合生成器

- 假设我们想生成集合 {1, ..., n} 的所有组合。
- 或者其他任何包含 n 个元素的集合。
- 组合就是子集。
- 并且，一个有 n 个元素的集合的子集可以用长度为 n 的位串来指定。
  - 每一位表示该元素是否在子集中。
- 因此，我们可以通过枚举所有长度为 n 的位串来枚举所有组合。

## 递归位串枚举器

```
procedure recEnumBitStrings(soFar,n)
{enumerate all strings consisting of soFar concatenated with a bit-string of length n}
if n=0 then begin print soFar; return end
enumBitStrings(soFar·‘0’, n−1)
enumBitStrings(soFar·‘1’, n−1)
procedure enumBitStrings(n∈N)
recEnumBitStrings(ε, n) {soFar=empty str}
```

## 生成下一个位串

请注意，这本质上只是一个二进制增量（“加 1”）操作。

```
procedure nextBitString(bₙ₋₁…b₀: bit string)
  i := 0;                     {start at right end of string}
  while bᵢ = 1 and i < n begin    {trailing 1s}
    bᵢ := 0; i := i + 1 end       {change to 0s}
  if i = n then return “no more” else begin
    bᵢ = 1; return bₙ₋₁…b₀ end   {chg. 0→1}
```

## 生成 $r$-组合

- 我们如何列出集合 $\{1, ..., n\}$ 的所有 $r$-组合？
- 由于组合中元素的顺序无关紧要，我们总可以按从小到大的顺序列出它们。
- 因此，我们可以先枚举可能的最小元素，然后对每一个最小元素枚举可能的下一个最小元素，以此类推。

## 递归 r-组合生成器

```
procedure recEnumRCombs(min,j,r,n)
    if j>n then print comb₁,...,combₙ; return
    for i:=min to n−r+1 begin
        combⱼ = i
        recEnumRCombs(i+1, j+1, r−1, n)
    end
```

## 生成下一个 $r$-组合

```
procedure nextRComb({a₁,...,aᵣ}⊂{1,...,n}
                 with aᵢ < aᵢ₊₁)
{Find the last item that can be inc’d}
i := r; while aᵢ = n - r + i do i := i - 1
aᵢ := aᵢ + 1                 {Increment it}
for j := i + 1 to r           {Set remaining items}
    aⱼ := aⱼ + j - i           {to the subsequent #’s}
return {a₁,...,aᵣ}
```

## 中文课件

- 4、计数原理/计数
- 4.1 基本计数原理
- 计数基础
- 4.2 包含与排斥原理
- 容斥原理
- 4.3 鸽洞原理（鸽巢原理）

- 求和规则/和规则
- 如果第一项任务有 n 种完成方式，第二项任务有 m 种完成方式，并且这两项任务不能同时进行，那么完成其中任一任务共有 n+m 种方式。
- $|A₁ ∪ A₂| = |A₁| + |A₂|$ 其中 $A₁ ∩ A₂ = ∅$

## 示例 1

- 例3 单循环程序

- 求和规则的推广
- $|A_1 ∪ A_2 ∪ ... ∪ A_n| = |A_1| + |A_2| + ... + |A_n|$
- 其中 $A_i ∩ A_j = ∅$
- $i ≠ j$, $i,j = 1,2,...,n$

