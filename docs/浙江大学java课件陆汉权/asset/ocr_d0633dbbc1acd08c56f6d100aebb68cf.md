# # Java实例——抛出多个异常

```
public class Exception3
{
   public static int Sum(int n){
   if (n < 0)
   throw new IllegalArgumentException("n应该为正整数！ ");
   int s = 0;
   for (int i=0; i<=n; i++) s = s + i;
   return s;
   }
}
```