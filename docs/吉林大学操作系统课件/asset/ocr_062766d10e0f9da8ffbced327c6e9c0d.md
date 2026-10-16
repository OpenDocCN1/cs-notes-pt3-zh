# Managing Physical Memory

+   - Whenever two allocated partner regions are both freed up they are combined to form a larger region.（两个相邻的伙伴被释放时，合并为一个大空闲区）
+   - If a memory request cannot be satisfied by allocating an existing small free region, then a larger free region will be subdivided into two partners to satisfy the request.（小区域不能满足时，分割大区域）