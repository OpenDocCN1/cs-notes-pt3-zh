```
class Person
{
private:
char *name;int age;int height;
public:
Person(int age,char *name,int height)
{
this->name = new char[strlen(name) + 1];
strcpy(this->name,name);
this->age = age;
this->height = height;
}
~Student()
{
delete name;
}
};
```