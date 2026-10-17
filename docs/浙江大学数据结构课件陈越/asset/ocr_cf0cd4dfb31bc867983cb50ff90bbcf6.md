# # 核心算法

# # 1. 计算最优编码长度

```
MinHeap H = CreateHeap( N ); /* 创建一个空的、容量为N的最小堆 */
H = ReadData( N ); /* 将f[]读入H->Data[]中 */
HuffmanTree T = Huffman( H ); /* 建立Huffman树 */
int CodeLen = WPL( T, 0 );
```

```
int WPL( HuffmanTree T, int Depth )
{
    if ( !T->Left && !T->Right )
        return (Depth*T->Weight);
    else /* 否则T一定有2个孩子 */
        return ( WPL(T->Left, Depth+1)
            + WPL(T->Right, Depth+1));
}
```

![](bbox=[0.614, 0.552, 0.772, 0.781])

Copyright @ 2014, 浙江大学计算机科学与技术学院  
All Rights Reserved