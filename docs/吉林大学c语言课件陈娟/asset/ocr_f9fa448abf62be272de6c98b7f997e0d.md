```
int delSamEle(int n, int a[]){
    int count=0;
    int i=0,j=0,k=0;
    for(i=0;i<n-count;i++){
        for(j=n-1-count;j>i;j--){
            if(a[i]==a[j]){
                for(k=j;k<n-1-count;k++){
                    a[k]=a[k+1];
                }
                a[n-1-count]=SPE;
                count++;
            }
        }
    }
    return count;
}
```