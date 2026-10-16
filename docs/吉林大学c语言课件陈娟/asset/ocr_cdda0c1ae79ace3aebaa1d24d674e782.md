队列中元素的类型为type of element并有如下说明：

```
#define size ...                 /* 队列的尺寸 */
type of element queue[size];     /* 队列 */
int inpointer,                   /* 送入指针 */
    outpointer,                  /* 取出指针 */
    count;                       /* 队列中现存数据数计数器 */
```

有关队列的操作有：

+   - 入 队
+     将一个 type of elemet 类型的数据送入队列的队尾
+   - 出 队
+     从队头取出一个数据使用，并将该数据从队列移掉