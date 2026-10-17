```
void input(int *data,int n);
void sort (int *data,int n);
void display(int *data,int n);

main()
{
    int DataCounter;
    int *data;
    estring str = "Please input the number of integers to be sorted:\n";
    cout <<str ;
    scanf("%d",&DataCounter);
    printf("Please input the number of integers: \n");
    data = new int[DataCounter];
    input(data,DataCounter);
    sort(data,DataCounter);
    printf("The sorted integers are:\n");
    display(data,DataCounter);

    delete data;
    return true;
}
/*函数 -- 输入数组*/
void input(int *data,int n)
{
    int i;
    for(i=0;i<n;i++)
    scanf("%d",&data[i]);
}
/*函数 -- 数组排序*/
void sort (int *data,int n)
{
    int i,j,temp;
    for (i = n;i > 0;i--)
    {
    for (j = 0;j < i - 1;j++)
    if (data[j] > data[j+1])
    {
    temp = data[j];
    data[j] = data[j+1];
    data[j+1] = temp;
    }
    }
}
```