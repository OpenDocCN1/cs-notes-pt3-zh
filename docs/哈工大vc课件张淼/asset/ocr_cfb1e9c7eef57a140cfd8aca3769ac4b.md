# # 类作用域

```
```cpp
class Student
{
private:
int number,score;
public:
void init();
};
void Student::init()
{
number = 1001;
score = 100;
}```
```