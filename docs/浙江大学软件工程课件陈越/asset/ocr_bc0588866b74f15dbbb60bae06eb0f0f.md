# ## 3.5 Loops-----While and For

+   - **Example 2:** see chap2_2 2.4

```
/* shellshort: sort v[0]...v[n-1] into increasing order */
void shellshort(int v[],int n)
{
    int gap,i,j,temp;
    for(gap=n/2;gap>0;gap/=2)
    for(i=gap;i<n;i--)
    temp=v[j];
    v[j]=v[j+gap];
    v[j+jap]=temp;
    }
}
```