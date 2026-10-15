# 二分搜索 - 递归

```
```cpp
int RBS(int *arr,int begin,int end, int num){
    int mid = begin + (end - begin)/2;
    if (begin <= end){
        if (arr[mid] == num)
            return mid;
        if (arr[mid] < num)
            begin = mid + 1;
        else
            end = mid - 1;
        RBS(arr,begin, end, num);
    }else
        return -1;
}
int RecursiveBinarySearch(int *arr,int length,int num){
    return RBS(arr, 0, length-1, num);
}
```
```