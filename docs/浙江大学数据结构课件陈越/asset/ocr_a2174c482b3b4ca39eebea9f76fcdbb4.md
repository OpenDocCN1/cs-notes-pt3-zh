# # 二分查找算法

```
int BinarySearch ( StaticTable * Tbl, ElementType K)
{
    /*在表Tbl中查找关键字为K的数据元素*/
    int left, right, mid, NoFound=-1;
    left = 1;
    right = Tbl->Length;
    while ( left <= right )
    {
        mid = (left+right)/2; /*计算中间元素坐标*/
        if( K < Tbl->Element[mid]) right = mid-1; /*调整右边界*/
        else if( K > Tbl->Element[mid]) left = mid+1; /*调整左边界*/
        else return mid; /*查找成功，返回数据元素的下标*/
    }
    return NotFound; /*查找不成功，返回-1*/
}
```

二分查找算法具有对数的时间复杂度O(logN)