# 6.2.4 按位逻辑运算符

+   - 按位逻辑运算符&（交）、|（或）、^（异或）、~（补）、>>和<<可以应用于整型和枚举（bool, char, short, int, long, enum）
+   - 方便的操作有可能非常重要，但是，为了可靠性、可维护性、可移植性等，应该将它保持在系统的底层中
+   - 位域也可以用于非在一个机器字里移位和掩盖，以便抽取一段二进制位的方便方式

# 按位逻辑运算符示例

```
enum ios_base :: iostate {
    goodbit=0, eofbit=1, failbit=2, badbit=4
};

state = goodbit;
//...
if(state & (badbit|failbit)) // stream有问题

unsigned short middle(long a)
{
    return (a>>8) & 0xffff;
} // 获取a中的第8bit到第23bit
```

# 6.2.5 增量和减量

+   - ++运算符用于直接表示加法，使人不必通过加和赋值的组合去同时表示两个操作，例如：n += 1的意思是value = value + 1，nvalue = nvalue + 1。减量也类似地采用--运算符
+   - 运算符++都可以用作前缀或者后缀运算符，++x的值是（增量之后的）新值。例如：y=x++等价于y=(x+=1)，x++的值是x原有的值，例如：y=x++等价于y=(t=x,x+=1)，其中t是一个与x同类型的变量

# 增量和减量

+   - 运算符++和--也可以用到在对数组元素进行操作的指针上：p++，使指向下一个元素

```
void cpv(char* p, const char* q){
    while(*p++ = *q++);
}

int length=strlen(q);
for(int i=0;i<=length;i++)
    p[i] = q[i]
// q被遍历了两遍，效率低
```