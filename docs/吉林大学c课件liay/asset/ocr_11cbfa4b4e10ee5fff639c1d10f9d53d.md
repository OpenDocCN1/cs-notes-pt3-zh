# 2.对象的引用以及返回对象的函数

```
class Student
{
public:
    int age;
    char name[9];
    float score;
};
```

```
int main()
{
    void add(Student&);
    Student get();
    Student a[30];
    for(i=0;i<30;i++)
        add(a[i]=get());
    return 0;
}
```

```
void add (Student &b)
{
    if(b.age<20)
        b.age++;
}
```

```
Student get()
{ Student temp;
    cin>>temp.age;
    cin>>temp.name;
    cin>>temp.score;
    return(temp);
}
```