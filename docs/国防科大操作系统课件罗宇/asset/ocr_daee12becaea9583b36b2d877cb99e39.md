# (2) kmem_cache_alloc() 与 kmem_cache_free()

当需要分配一个拥有专用 slab 队列的对象时，应该通过 kmem_cache_alloc() 函数，相反的动作则是 kmem_cache_free() 函数。

分配的对象来自 slab 缓冲，释放的对象归还 slab 缓冲，通过某种标识表明对象是可用还是已被占用。

![](bbox=[0.0, 0.0, 0.13, 0.55])