```
float Student::sum=0;    //对静态数据成员初始化
int Student::count=0;    //对静态数据成员初始化

int main( )
{
    Student stud[3]={    Student(1001, 18, 70),
                    Student(1002, 19, 78),
                    Student(1003, 20, 98)  };
    for(int i=0;i<3;i++)
        stud[i].total( );

    cout<<"the average score of is "
        << Student::average( )<<endl;
    return 0;
}
```