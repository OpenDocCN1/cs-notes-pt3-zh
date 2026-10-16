# # 选择问题

给定线性序集中n个元素和一个整数k， 1≤k≤n， 要求找出这n个元素中第k小的元素

```
template<class(Type>
Type(RandomizedSelect(Type(a[],int(p,int(r,int(k)
{
(((((if(p==r)(return(a[p];
(((((int(x=RandomizedPartition(a,p,r),
(((((i=x-p+1;
(((((if(k<=j)(return(RandomizedSelect(a,p,x,k);
(((((else(return(RandomizedSelect(a,x+1,r,k-i);
}
```

在最坏情况下，算法randomizedSelect需要O(n²)计算时间但可以证明，算法randomizedSelect可以在O(n)平均时间内找出n个输入元素中的第k小元素。