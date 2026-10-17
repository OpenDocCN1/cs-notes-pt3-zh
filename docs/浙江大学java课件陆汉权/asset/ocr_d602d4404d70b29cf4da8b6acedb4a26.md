# 例--展示数组参数传递地址的特性

```
class ArrayC6 {
    public static void main(String[] args){
        int c[][]={{1,2,3,4,5},{6,7,8,9,10}};
        int i, j;
        System.out.println("调用arrayMultiply之前的数组");
        for (i=0; i<c.length; i++){
            for(j=0; j<c[i].length; j++)
                System.out.print(c[i][j]+" ");
            System.out.println();
        }
        arrayMultiply(c);  // 调用数组
```