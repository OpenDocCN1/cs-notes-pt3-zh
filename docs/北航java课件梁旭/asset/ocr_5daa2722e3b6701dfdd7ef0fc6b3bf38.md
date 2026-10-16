# 例子：

```
public class ArrayTest
{
    public static void main(String args[])
    {
        int i;
        int a[] = new int[5];//定义及创建
        for( i=0; i<5; i++ )
        {
            a[i]=i; //直接赋值
        }
        for( i=a.length-1; i>=0; i-- ) //a.length是数组a的长度
        {
            System.out.println("a["+i+"] = "+a[i]);
        }
    }
}
```

运行结果：  a[4]=4;
        ...
        a[0]=0;