# # 第5章 继承

# ## 5.11 类与类的关系

# ### 类的组合（has-a关系）

```
class Engine{
public: void work(); };
class Wheel{
public: void roll(); };
class Automobile{
private: Engine * engine;
Wheel* wheel;
public: void move(){
engine->work();
for(int i=0;i<4;i++) wheel[i]->roll();
}
};
```