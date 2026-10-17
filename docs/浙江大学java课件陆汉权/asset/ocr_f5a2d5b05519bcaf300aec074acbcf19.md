# 例：求2-50之间的所有素数

```
public class Primes {
public static void main(String args[]) {
final int MAX=50;
int i, k;
boolean yes;

for(k=2; k<MAX; k++){ //外循环，k:2~50
yes=true;
i=2;
while (i<=k-1 && yes){ // 内循环，i:2~k
if (k%i++ ==0) yes=false; // 不是素数
}
if (yes) System.out.print(k+" ");
}
}
}
```