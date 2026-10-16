# 4.1 数组

# 多维数组的初始化

✓静态初始化：

```
int[][] intArray={{2,3}, {1,5}, {3,4}};
```

intArray为一个3行2列的数组

| 2 | 3 |
|---|---|
| 1 | 5 |
| 3 | 4 |

最外层括号所包含的元素是数组的第一维的各元素；
最内层括号对应于数组最后一维。

```
int intArray1[][]={{1,2,3},{4,5,6,7},{8,9,10,11,12}};
for(int i=0;i<intArray1.length;i++){
    for(int j=0;j<intArray1[i].length;j++){
        System.out.print(intArray1[i][j]+" ");
    }
    System.out.print("\n");
}
```