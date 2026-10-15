

## mm_free()
```
27    else if (!prev_alloc && next_alloc) { /* Case 3 */
28        size += GET_SIZE(HDRP(PREV_BLKP(bp)));
29        PUT(FTRP(bp), PACK(size, 0));
30        PUT(HDRP(PREV_BLKP(bp)), PACK(size, 0));
31        return(PREV_BLKP(bp));
32    }
33
34    else { /* Case 4 */
35        size += GET_SIZE(HDRP(PREV_BLKP(bp))) +
36                GET_SIZE(FTRP(NEXT_BLKP(bp)));
37        PUT(HDRP(PREV_BLKP(bp)), PACK(size, 0));
38        PUT(FTRP(NEXT_BLKP(bp)), PACK(size, 0));
39        return(PREV_BLKP(bp));
40    }
41 }
```

## mm_malloc()
```
void *mm_malloc (size_t size)
{
    size_t asize; /* adjusted block size */
    size_t extendsize; /* amount to extend heap if no fit */
    char *bp;

    /* Ignore spurious requests */
    if (size <= 0)
        return NULL;

    /* Adjust block size to include overhead and alignment reqs. */
    if (size <= DSIZE)
        asize = DSIZE + OVERHEAD;
    else
        asize = DSIZE * ((size + (OVERHEAD) + (DSIZE-1)) / DSIZE);

    /* Search the free list for a fit */
    if ((bp = find_fit(asize)) != NULL) {
        place (bp, asize);
        return bp;
    }

    /* No fit found. Get more memory and place the block */
    extendsize = MAX (asize, CHUNKSIZE);
    if ((bp = extend_heap (extendsize/WSIZE)) == NULL)
        return NULL;
    place (bp, asize);
    return bp;
}
```

## mm_alloc()
```
1. static void *find_fit(size_t asize)
2. {
3.     void *bp ;
4.
5.     /* first fit search */
6.     for (bp = heap_listp; GET_SIZE(HDRP(bp)) > 0 ; bp = NEXT_BLKP(bp) ) {
7.         if (!GET_ALLOC(HDRP(bp)) && (asize <= GET_SIZE(HDRP(bp)))) {
8.             return bp;
9.         }
10.    }
11.    return NULL; /*no fit */
12. }
```

## mm_alloc()
```
1.  static void place(void *bp, size_t asize)
2.  {
3.      size_t csize = GET_SIZE(HDRP(bp));
4.
5.      if ( (csize - asize) >= (DSIZE + OVERHEAD) ) {
6.          PUT(HDRP(bp), PACK(asize, 1));
7.          PUT(FTRP(bp), PACK(asize, 1));
8.          bp = NEXT_BLKP(bp);
9.          PUT(HDRP(bp), PACK(csize-asize, 0));
10.         PUT(FTRP(bp), PACK(csize-asize, 0));
11.     } else {
12.         PUT(HDRP(bp), PACK(csize, 1));
13.         PUT(FTRP(bp), PACK(csize, 1));
14.     }
15. }
```

## 动态内存分配

## 大纲
- 显式空闲链表
- 分离空闲链表
- 建议阅读：9.9

## 显式空闲链表
- 使用空闲块内的指针在空闲块之间建立显式链表
- 使用数据空间存放链接指针
- 通常是双向链表
- 仍需要边界标签用于合并
- 必须认识到，链接不一定与块的顺序相同

## 显式空闲链表
![](img/b3f8b91675c485f1e811aa092ebbf3d4_1036_0.png)

## 使用显式空闲链表释放
- 将新释放的块放在空闲链表的何处
  - LIFO（后进先出）策略
    - 将释放的块插入空闲链表的开头
    - 优点：简单且时间恒定
    - 缺点：研究表明碎片比地址有序更严重。

## 使用显式空闲链表释放
- 将新释放的块放在空闲链表的何处
  - 地址有序策略
    - 插入释放的块，使空闲链表中的块始终按地址顺序排列
      - 即 addr(pred) < addr(curr) < addr(succ)
    - 缺点：需要搜索
    - 优点：研究表明碎片比 LIFO 更好

## 分离存储
- 每个大小“类”都有自己的块集合
  - 通常为每个小尺寸（2,3,4,...）都有单独的集合
  - 对于较大尺寸通常为每个 2 的幂设置一个集合

## 简单分离存储
- 每个大小类都有单独的堆和空闲链表
- 不进行分割
- 分配大小为 n 的块时：
  - 如果大小为 n 的空闲链表不为空，
    - 分配列表上的第一个块（注意，列表可以是隐式的或显式的）
  - 如果空闲链表为空，
    - 获取一个新页面
    - 从页面中的所有块创建新的空闲链表
    - 分配列表上的第一个块
  - 时间恒定

