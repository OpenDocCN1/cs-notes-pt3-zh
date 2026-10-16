
## 习题10.2：输入3个字符串，按由小到大的顺序输出。

```
void swap(char *ps1,char *ps2);
main()
{
    char s1[]="xyz",s2[]="rst",s3[]="abc";
    if(strcmp(s1,s2)>0) swap(s1,s2);
    if(strcmp(s1,s3)>0) swap(s1,s3);
    if(strcmp(s2,s3)>0) swap(s2,s3);
    printf("\n%10s %10s %10s",s1,s2,s3);
}
void swap(char *ps1,char *ps2)
{char ps[100];
strcpy(ps,ps1);strcpy(ps1,ps2);strcpy(ps2,ps);
}
//char *ps;
//ps=ps1;ps1=ps2;ps2=ps;
```

## strcmp(字符串1，字符串2)

- 字符串比较的规则:
  - 对两个字符串自左至右逐个字符按ASCII码值大小比较，直到出现不同的字符或遇到‘\0’为止；
  - 若全部字符相同，则认为相等；
  - 若出现不同的字符，则以第一个不相同的字符的比较结果为准。
- 比较的结果由函数名带回:
  - 1）如果字符串1=字符串2，函数值为0；
  - 2）如果字符串1>字符串2，函数值为一正整数；
  - 3）如果字符串1<字符串2，函数值为为一负整数；

## 习题10.6：写一个函数，求字符串的长度，在main函数中输入字符串，并输出其长度。

```
int len(char *ps);
void main()
{
    char str[30];
    gets(str);
    printf("\n len=%d",len(str));
}
int len(char *ps)
{
    int n=0;
    while(*ps++) n++;
    return n;
}
```

## 习题10.8：输入一行文字，找出其中大写字母、小写字母、空格、数字以及其他字符各有多少？

```
void main()
{ char s[100],*p;
    int lowc=0, upc=0, space=0, num=0,other=0;
    gets(s);
    p=s;
    while(*p)
    { if(*p>='A' && *p<='Z') upc++;
      else if(*p>='a' && *p<='z') lowc++;
      else if(*p>='0' && *p<='9') num++;
      else if(*p==' ') space++;
      else other++;
      p++;
    }
    printf("\n upc=%d lowc=%d num=%d space=%d other=%d", upc, lowc, num, space,other);
}
```

## 习题10.11：对10个等长的字符串排序并输出。

```
void sort(char (*p)[60]);
main()
{
    char s[10][60],i;
    for(i=0; i<10; i++) gets(s+i);
    sort(s);
    for(i=0; i<10; i++) puts(s+i);
}

void sort(char (*p)[60])
{
    int i,j;
    char s[60];
    for(i=0; i<9; i++)
        for(j=i+1; j<10; j++) //冒泡法
            if(strcmp(p[i],p[j])>0)
            {
                strcpy(s,p[i]); strcpy(p[i],p[j]); strcpy(p[j],s);
            }
}
```

## 10.12: 用指针数组处理上一个题目，字符串不等长。

```
void sort(char *p[],int n);
main()
{
    char *s[10]={"  DDD "," AAA ","878787"},*ps[10],i;
    for(i=0;i<10;i++) ps[i]=s[i];
    sort(ps,3);//
    for(i=0;i<3;i++) puts(ps[i]);
}
void sort(char *pt[],int n)
{
    int i, j;
    char *s;
    for(i=0;i<n-1;i++)
        for(j=i+1;j<n;j++)
            if(strcmp(pt[i],pt[j])>0)
                s=pt[i], pt[i]=pt[j], pt[j]=s;
}
```

## 习题10.16：输入一个字符串，将其中的数字串转换成数值送数组a。

```
void main()
{
  char s[128],*ps=s;
  int a[100], i, n;
  gets(s);//"abc987def6543ghijk210"
  for(i=0,n=0;*ps;ps++)//如果*ps='\0'=0，循环终止
    if(*ps>='0' && *ps<='9')
      n=n*10+*ps-'0';
    else//遇到非数字时，数字转换完成
      { if(n>0) a[i++]=n;//将数值存入数组a
        n=0;//重新将n置零
      }
  if(n>0) a[i++]=n;//将字符串末尾的数值存入数组
  for(n=0; n<i; n++) printf("%6d",a[n]);
}
```

## 习题10.18：根据输入的月份输出月的英文名。

```
void main()
{ char *month[]={"January","February","March",
    "April", "May","June","July", "August",
    "Septermber", "October","Noverber",
    "Decermber"};

int mon;
scanf("%d",&mon);
if(mon<1 ||mon>12) printf("month error!");
else puts(month[mon-1]);
}
```

## 作业

## （上机运行以下程序，要求使用指针）

- （1）写一函数，将一个3×4的矩阵转置，将数据存储到一个4×3的矩阵后，将两个矩阵输出。
- （2）输入5个字符串，按由大到小的顺序输出。
- （3）对n个等长的字符串排序并输出，n在2~10之间可变。
- （4）写一个函数，接受一个已排序的整形数数组和一个整数，将该整数插入数组的适当位置，将该数组在变化前后分别输出。

## 1. State the following statements are true or false.

判断下列说法是真还是假

- a) Pointer variables are declared using the address operator.
  
  指针变量用地址运算符(&)来定义。
  
- b) The underlying type of a pointer variable is void.
  
  指针变量名不能使用下划线。
  
- c) Pointers to pointers is a term used to describe pointers whose contents are the address of another pointer.
  
  指向指针的指针是这样一种参数，它用于描述一种把其他指针的地址作为内容的指针。
  
- d) It is possible to cast a pointer to float as a pointer to integer.
  
  可以把float型的指针用作指向integer型数的指针。

- e) An integer can be added to a pointer.
指针可以与一个整数相加。

- f) A pointer can never be subtracted from another pointer.
指针不能与指针相减。

- g) When an array is passed as an argument to a function, a pointer is passed.
当把数组作为变量传递给一个函数时，就等于传递了一个指针。

- h) Pointers cannot be used as formal parameters in headers to function definition.
进行函数定义时，函数头内的形参不能使用指针。
