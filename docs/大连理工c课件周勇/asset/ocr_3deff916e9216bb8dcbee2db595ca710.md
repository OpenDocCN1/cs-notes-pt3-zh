# # 析构函数

```
```cpp
class Student
{
public:
    Student();
    Student(int, char*);
    ~Student();
    void display();
private:
    int num;
    char name[10];
};
```
```

```
```cpp
class Student
{
public:
    Student();
    Student(int, char*);
    ~Student();
    void display();
private:
    int num;
    char* name;
};
```
```