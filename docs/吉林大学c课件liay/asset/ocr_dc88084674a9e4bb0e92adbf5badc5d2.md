```
```cpp
class Student{
    int move_tel;
public:
    Student(int i){tel=i;}
    int id;
    void O(){cout<<tel<<endl;}
protected:
    int tel;
};
class Master : public Student{
    string topic;
public:
    Master(int j,int k):Student(k){tel = j;}
    string dept;
    void O(){
        cout<<tel<<endl;
        Student::O();
        cout<<Student::tel<<endl;
    }
protected:
    int tel;
};
void main()
{
    Master a(13312345,13012345); a.O(); a.Student::O();
}
```
```

> 如果父类中出现Master::tel形式的访问，错误！！！