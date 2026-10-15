

## Nested-Loop Join（续）

- 在最坏情况下，如果内存只能容纳每个关系的1个块，则估计成本为
  $n_r \cdot b_s + b_r$ 次块传输，外加
  $n_r + b_r$ 次寻道
- 如果较小的关系完全适合内存，则将其用作内层关系。
  - 将成本降至 $b_r + b_s$ 次块传输和 2 次寻道
- 假设最坏情况内存可用性成本估计为
  - 以 student 为外层关系：
    - 5000 × 400 + 100 = 2,000,100 次块传输，
    - 5000 + 100 = 5100 次寻道
  - 以 takes 为外层关系
    - 10000 × 100 + 400 = 1,000,400 次块传输和 10,400 次寻道
- 如果较小的关系（student）完全适合内存，成本估计将为 500 次块传输。
- 块嵌套循环算法（下一张幻灯片）更可取。

## Block Nested-Loop Join

- 嵌套循环连接的变体，其中内层关系的每个块都与外层关系的每个块配对。

```
for each block B_r of r do begin
  for each block B_s of s do begin
    for each tuple t_r in B_r do begin
      for each tuple t_s in B_s do begin
        Check if (t_r, t_s) satisfy the join condition
        if they do, add t_r · t_s to the result.
      end
    end
  end
end
```

## Block Nested-Loop Join（续）

- 最坏情况估计：$b_r * b_s + b_r$ 次块传输 + $2 * b_r$ 次寻道
  - 内层关系 $s$ 中的每个块对于外层关系中的每个块都会被读取一次
- 最佳情况：$b_r + b_s$ 次块传输 + 2 次寻道。
- 对嵌套循环和块嵌套循环算法的改进：
  - 在块嵌套循环中，使用 $M - 2$ 个磁盘块作为外层关系[content]

## Nested-Loop Join（续）

- 在最坏情况下，如果内存只能容纳每个关系的1个块，则估计成本为
  $n_r \cdot b_s + b_r$ 次块传输，外加
  $n_r + b_r$ 次寻道
- 如果较小的关系完全适合内存，则将其用作内层关系。
  - 将成本降至 $b_r + b_s$ 次块传输和 2 次寻道
- 假设最坏情况内存可用性成本估计为
  - 以 student 为外层关系：
    - 5000 × 400 + 100 = 2,000,100 次块传输，
    - 5000 + 100 = 5100 次寻道
  - 以 takes 为外层关系
    - 10000 × 100 + 400 = 1,000,400 次块传输和 10,400 次寻道
- 如果较小的关系（student）完全适合内存，成本估计将为 500 次块传输。
- 块嵌套循环算法（下一张幻灯片）更可取。

## Block Nested-Loop Join

- 嵌套循环连接的变体，其中内层关系的每个块都与外层关系的每个块配对。

```
for each block B_r of r do begin
  for each block B_s of s do begin
    for each tuple t_r in B_r do begin
      for each tuple t_s in B_s do begin
        Check if (t_r, t_s) satisfy the join condition
        if they do, add t_r · t_s to the result.
      end
    end
  end
end
```

## Block Nested-Loop Join（续）

- 最坏情况估计：$b_r * b_s + b_r$ 次块传输 + $2 * b_r$ 次寻道
  - 内层关系 $s$ 中的每个块对于外层关系中的每个块都会被读取一次
- 最佳情况：$b_r + b_s$ 次块传输 + 2 次寻道。
- 对嵌套循环和块嵌套循环算法的改进：
  - 在块嵌套循环中，使用 $M - 2$ 个磁盘块作为外层关系的块大小，其中 $M =$ 内存大小（以块为单位）；使用剩余的两个块来缓冲内层关系和输出
    - 成本 = $\lceil b_r / (M-2) \rceil * b_s + b_r$ 次块传输 + $2 \lceil b_r / (M-2) \rceil$ 次寻道
  - 如果等值连接属性构成键或内层关系，则在首次匹配时停止内层循环
  - 交替向前和向后扫描内层循环，以利用缓冲区中剩余的块（采用 LRU 替换）
  - 如果可用，使用内层关系的索引（下一张幻灯片）

## Example of Nested-Loop Join Costs

⋈

- 计算 *student* ⋈ *takes*，以 *student* 为外层关系。
- 设 *takes* 在属性 `/ID` 上有一个主键 B⁺-树索引，每个索引节点包含 20 个条目。
- 由于 *takes* 有 10,000 个元组，树的高度为 4，并且还需要一次额外访问来找到实际数据。
- *student* 有 5000 个元组
- 块嵌套循环连接的成本
  - 400*100 + 100 = 40,100 次块传输 + 2 * 100 = 200 次寻道
    - 假设最坏情况内存
    - 内存更多时可能显著更少
- 索引嵌套循环连接的成本
  - 100 + 5000 * 5 = 25,100 次块传输和寻道。
  - CPU 成本可能低于块嵌套循环连接的成本

