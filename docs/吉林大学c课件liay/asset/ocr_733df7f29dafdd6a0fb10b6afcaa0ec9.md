```
class A {
public:
    A():s(9) {cout<<"A is Constructing!"<<endl;}
    int R_s(){return(s);};
private:
    int s;
};
class Student{
public:
    static A noOfStudents;
private:
    int x;
};
A Student::noOfStudents;//不允许省略
void main()
{ cout<<"Main Function is runing!"<<endl;
  cout<<Student::noOfStudents.R_s()<<endl;
}
```

静态成员在main之前构造
生命周期等同于全局对象