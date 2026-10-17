# # 第3章 类与对象

# ## 3.6 对象数组

# ## 例3.8 计算一组学生的总成绩和平均成绩

```
class Student{
private:
char name[20];
int age;
float score;
public:
Student(char * n, int a, int s){
strcpy(name,n);
age=a; score=s; }
float getScore(){
return score; }
};
```

```
int main(){
Student
stud[3]={ Student("zhang
san",20,60), Student("Li
si",19,70),
Student("Wang wu",18,78) };
float sum=0,average;
int i;
for(i=0;i<3;i++)
sum+=stud[i].getScore();
average=sum/3;
cout<<"sum="<<sum<<"
average="<<average<<endl,
return 0; 大连理工大学软件学院
```