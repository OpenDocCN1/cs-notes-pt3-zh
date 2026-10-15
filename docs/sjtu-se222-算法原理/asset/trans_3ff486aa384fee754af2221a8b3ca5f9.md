

## 费诺编码

| 消息符号 | 各个消息概率 $p(x_i)$ | 第一次分组 | 第二次分组 | 第三次分组 | 第四次分组 | 第五次分组 | 二元码字 | 码长 $K_i$ |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| $x_1$ | 0.25 | 0 | 0 |  |  |  | 00 | 2 |
| $x_2$ | 0.2 | 0 | 1 |  |  |  | 01 | 2 |
| $x_3$ | 0.2 | 1 | 0 | 0 |  |  | 100 | 3 |
| $x_4$ | 0.1 | 1 |  | 1 |  |  | 101 | 3 |
| $x_5$ | 0.1 | 1 |  | 0 |  |  | 110 | 3 |
| $x_6$ | 0.08 | 1 | 1 |  | 0 |  | 1110 | 4 |
| $x_7$ | 0.05 | 1 | 1 | 1 |  |  | 11110 | 5 |
| $x_8$ | 0.02 | 1 | 1 | 1 | 1 |  | 11111 | 5 |

**平均码长：**

$$\bar K=\sum_{i=1}^{s}p(x_i)K_i$$

$$=0.25\times2+0.2\times2+0.2\times3+0.1\times3+0.1\times3+0.08\times4+0.05\times5+0.02\times5$$

$$=2.77\ \text{码元/符号}$$

**信源熵：**

$$H(X)=-\sum_{i=1}^{s}p_i\log p_i$$

$$=0.050+0.464+0.464+0.332+0.332+0.292+0.216+0.113$$

$$=2.71\ \text{bit/符号}$$

**编码效率：**

$$\eta=\frac{H(X)}{\bar K}=\frac{2.71}{2.77}=0.98$$

## Huffman编码

- 概率排序
- 构建哈夫曼树，合并两个最小概率的事件，直到概率达到1为止
- 一个支路为0，一个支路为1
- 顺序记录路径上的1和0，即为哈夫曼码

## Huffman编码

| 信源符号 | 出现概率 | 码长 | 数字 |
|---|---|---|---|
| a₁ | 0.20 | 2 | 11 |
| a₂ | 0.19 | 2 | 10 |
| a₃ | 0.18 | 3 | 011 |
| a₄ | 0.17 | 3 | 010 |
| a₅ | 0.15 | 3 | 001 |
| a₆ | 0.10 | 4 | 0001 |
| a₇ | 0.01 | 4 | 0000 |

图 4.6 霍夫曼编码示例

## Huffman编码

```
1、根据权值初始化哈夫曼树
for(int i=0;i<n;i++)
{
    HTree[i].weight=a[i];
    HTree[i].LChild=-1;
    HTree[i].RChild=-1;
    HTree[i].parent=-1;
}
```

![](img/a8f1b433a70f1e5c410c8b43e41b650e_1094_0.png)

2、开始建立哈夫曼树，
int x,y;
for (int i=n;i<2*n-1;i++) {
    selectMin(x,y,0,i);//从1到i选择两个权值最小的
    HTree[x].parent=HTree[y].parent=i;
    HTree[i].weight=HTree[x].weight+HTree[y].weight;
    HTree[i].LChild=x;
    HTree[i].RChild=y;
    HTree[i].parent=-1;
}

## Huffman编码

```
二、建立哈夫曼编码表
void Huffman::CreateCodeTable(char b[], int n)
{
    HCodeTable = new HCode[n];
    for (int i = 0; i < n; i++)
    {
        HCodeTable[i].data = b[i]; //生成编码表
        int child = i;
        int parent = HTree[i].parent;
        int k = 0;
        while (parent != -1)
        {
            if (child == HTree[parent].lChild)
                HCodeTable[i].code[k] = '0'; //左孩子标“0”
            else
                HCodeTable[i].code[k] = '1'; //右孩子标“1”
            k++;
            child = parent;
            parent = HTree[child].parent;
        }
    }
}
```

![](img/a8f1b433a70f1e5c410c8b43e41b650e_1095_0.png)

## Huffman编码

四、解码：利用哈夫曼树进行解码，编码串左到右依次逐位判断，从根节点开始根据每一位是0还是1，确定是左分支还是右分支，直到到叶子节点为止，从编码表中找到对应字符并输出

```
void Huffman::Decode(char*s,char*d,int n)//s 为编码串
{
    while(*s!='0')
    {
        int parent=2*n-1-1;//根节点在 HTree 中的下标
        while(HTree[parent].LChild!=-1)
        {
            if(*s=='0')
                parent=HTree[parent].LChild;
            else
                parent=HTree[parent].RChild;
            s++;
        }
        *d=HCodeTable[parent].data;
        cout<<*d;
        d++;
    }
}
```

![](img/a8f1b433a70f1e5c410c8b43e41b650e_1096_0.png)

## Huffman编码特点

- 霍夫曼编码对不同的信源的编码效率是不同的。
- 当信源概率是 2 的负幂时，霍夫曼码的编码效率达到 100%；当信源概率相等时，其编码效率最低。
- 只有在概率分布很不均匀时，霍夫曼编码才会收到显著的效果。

- 解码时，必须参照这一霍夫曼编码表才能正确译码。
- 在信源的存储与传输过程中必须首先存储或传输这一霍夫曼编码表。在实际计算压缩效果时，必须考虑霍夫曼编码表占有的比特数。

## 提高编码效率

- X={x1,x2} = {黑,白}
- P(x1) = 0.9   P(x2) = 0.1
- H(X) = -0.9*log0.9 − 0.1*log0.1 = 0.469
- 码长至少要1位，则编码效率只有H(X)/1 = 46.9%

## 提高编码效率

![](img/a8f1b433a70f1e5c410c8b43e41b650e_1099_0.png)

{0,10,110,111}

平均编码长度：$l_2=0.81+0.09\times2+0.09\times3+0.01\times3=1.29\ \text{bit/pel}$，$l_2/2=0.645\ \text{bit/pel}$

编码效率：$\eta_2=\frac{H(X)}{l_2/2}=\frac{0.469}{0.645}=72.7\%$

## 提高编码效率

![](img/a8f1b433a70f1e5c410c8b43e41b650e_1100_0.png)

W³ = {0,100,101,110,11100,11101,11110,11111}

平均编码长度： l₃ = 0.729 + 3 × 3 × 0.081 + 5 × (3 × 0.009 + 0.001) = 1.598 bit/pel    l₃/3 = 0.5327 bit/pel。

编码效率： η₃ = H(X) / (l₃/3) = 0.469 / 0.5327 = 88.0%

## 游程编码

- 用一个符号值或串长代替具有相同值的连续符号
- 5555557777733322221111111
- （5，6）（7，5）（3，3）（2，4）（1，7）

