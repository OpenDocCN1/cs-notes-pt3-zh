```
```java
import java.util.*;
public class ArrayTest
{
    public static void main( String args[] )
    {
        int a[]={9,1,3,4,2,5,7,6,8};
        System.out.println("数组排序前为：");
        for(int i=0;i<a.length;i++)
            System.out.print(a[i]+" ");
        System.out.print("\n数组a排序后为：");

        Arrays.sort(a);//排序语句

        for(int i=0;i<a.length;i++)
            System.out.print(a[i]+" ");
        System.out.println();
    }
}
```
```