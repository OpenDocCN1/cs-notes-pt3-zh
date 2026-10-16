程序如下：

```
#include<stdio.h>
#define N 80
main()
{int a[N];
    int i, m;
    void sort(int b[], int k);
    void print(int b[], int k);
    printf("\n\nInput m(<80):");
    scanf("%d",&m);        /*输入要排序的元素的个数*/
    for (i=0; i<m; i++)
        scanf("%d", &a[i]); /*输入m个元素到数组a中 */
    sort(a, m);
    print(a, m);
}
```