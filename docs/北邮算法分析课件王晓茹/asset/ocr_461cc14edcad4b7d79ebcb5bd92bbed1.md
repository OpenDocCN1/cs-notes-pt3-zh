# # 合并排序

**基本思想：** 将待排序元素分成大小大致相同的2个子集合，分别对2个子集合进行排序，最终将排好序的子集合合并成为所要求的排好序的集合。

```
```java
public static void mergeSort(Comparable a[], int left, int right)
{
    if (left<right) //至少有2个元素
    int i=(left+right)/2; //取中点
    mergeSort(a, left, i);
    mergeSort(a, i+1, right);
    merge(a, b, left, i, right); //合并到数组b
    copy(a, b, left, right);  //复制回数组a
}
}
```
```