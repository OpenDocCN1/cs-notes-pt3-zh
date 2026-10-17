# # Indexed Allocation – Mapping (Cont.) 索引分配—映射 （续）

+   - Mapping from logical to physical in a file of unbounded length (block size of 512 words). （无限长度的文件从逻辑向物理的映射）

+   - 1. Linked scheme – Link blocks of index table (no limit on size). （链接策略—把索引块链接起来）（没有长度限制）

LA / (512 x 511) → Q₁, R₁

Q₁ = block of index table  
R₁ is used as follows:
R₁ / 512 → Q₂, R₂

Q₂ = displacement into block of index table  
R₂ displacement into block of file: