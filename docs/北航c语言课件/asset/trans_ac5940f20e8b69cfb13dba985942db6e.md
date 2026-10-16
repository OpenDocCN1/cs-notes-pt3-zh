

功能：按指定格式将数据写到指定文件中。  
或从指定文件按格式输入数据。  

**fprintf** 和 **fscanf** 函数执行 I/O 操作，当然它们作用于文件。

```
例如：`fprintf(fp, "%d,%6.2f",i,x);`
```

```
又如：`fscanf(fp, "%d,%f",&i,&x);`
```

```c
#include "stdio.h"
void main()
{char infile[15], outfile[15],radar[10],func[6];
FILE *fp1,*fp2;
    printf("请输入雷达数据文件名(*.txt)\n");
    scanf("%s",infile);
    if((fp1=fopen(infile,"r"))==NULL)
    {
        printf("cannot open this file\n");
        exit(0);
    }
}
```

```c
fscanf(fp1,"%s",radar);
fscanf(fp1,"%s",func);
fscanf(fp1,"%f",&frequ);
fscanf(fp1,"%f",&rmax);
fscanf(fp1,"%f",&sigma0);
fscanf(fp1,"%f",&pd0);
fscanf(fp1,"%e",&p_fa);
fscanf(fp1,"%f",&prf);
fscanf(fp1,"%f",&tao);
fscanf(fp1,"%f",&rpm);
fscanf(fp1,"%d",&type);
fscanf(fp1,"%f",&phi_b);
fscanf(fp1,"%f",&theta_b);
fscanf(fp1,"%f",&Emax);
fclose(fp1);
......
```

|  |  |
|---|---|
| AN_TPS-43E.txt |  |
| 4000 | 脉冲功率(kW) |
| 6310 | 最大增益 |
| 0.3125 | 带宽(MHz) |
| 3 | 中心频率(GHz) |
| 0.1 | 天线高度(km) |
| 440 | 最大作用距离(km) |
| 5 | 对应散射截面(m^2) |
| 0.5 | 对应发现概率 |
| 1e-006 | 对应虚警概率 |
| 1.1 | 水平波束宽度(deg) |
| 4.8 | 垂直波束宽度(deg) |
| 20 | 仰角扫描范围(deg) |
| 6 | 天线转速(rpm) |
| 1 | 斯威林模型(1~4) |
| 6.5 | 脉冲宽度(us) |
| 250 | 脉冲重复频率(Hz) |
| 2 | 脉冲积累数 |
| 1.20472e+023 | 系统特征常数(m^2) |

```c
printf("请输入输出数据文件名(*.txt)\n");
scanf("%s",outfile);
if((fp2=fopen(outfile,"w"))==NULL)
{
    printf("cannot open this file\n");
    exit(0);
}
```

```c
fprintf(fp2,"Radar:%s, Function=%s, Frequency=%5.1f MHz ",radar,func,frequ);
fprintf(fp2," PRF=%5.1f Hz, Tao=%4.1f us, RPM=%4.1f r/min\n",prf,tao,rpm);
fprintf(fp2,"swerling_case:%d, rmax=%6.1f km, sigma0=%5.1fdB, PD0=%5.1f, P_fa=%e, N number=%d\n",swerling_case,rmax,sigma0,pd0,p_fa,N);
for(j=0;j<X;j++) fprintf(fp2,"%4.0f,dBsm ",sigma[j]);
fprintf(fp2,"\n");
for(j=0;j<Z;j++)
{
    for(i=0;i<X;i++) fprintf(fp2,"\t%6.4f",pdd[i][j]);
    fprintf(fp2,"\n");
}
fclose(fp2);
......
}
```

## 四、 fputs函数 和 fgets函数

这两个函数是以字符串为单位进行文件读写的函数。

### 1. fputs函数

一般调用形式： fputs(字符串,文件指针);

功能： 向指定文件输出一个字符串。

例如： fputs(str,fp); (其中str是字符数组名)  
含义： 向fp 所指向的文件中输出str中的字符串。

### 2. fgets函数

调用形式： fgets(字符数组,字符串长度,文件指针);

功能： 从指定文件中读入一个字符串。

例如： fgets(str,n,fp); (其中str是字符数组名)  
含义： 从fp指向的文件读取长度为n-1的字符串，最后加一个 ‘\0’存入字符数组str中。

## 五、文件的定位函数

### 1. rewind函数

一般调用形式：

```
rewind(文件指针);
```

功能：使位置指针重新返回文件的开头。

### 2. fseek函数

一般调用形式：

```
fseek(文件指针，位移量，起始点);
```

起始点：用0、1、2或其对应的名字SEEK_SET、SEEK_CUR、SEEK_END代替，分别表示文件开始、文件当前位置、文件末尾。

位移量：指以起始点为基点，向前（-）或向后移动的字节数。ANSI C标准规定在数字末尾加一个字母L，表示long型。

功能：把文件的读写位置指针移到指定的位置。

例如： fseek(fp,128L,SEEK_SET);  
将位置指针移到离文件头128个字节处。

例如： fseek(fp,-10L,2);  
将位置指针从文件末尾处向前退10个字节。

注意： fseek函数一般用于二进制文件。

### 3. ftell函数

一般调用形式： ftell(文件指针);

功能： 返回文件位置指针的当前值。

例如： pos=ftell(fp);  
获取fp指向文件的当前读写位置，并将其值赋给变量pos。

## 作业：

- 设文件vehicle_1.txt和vehicle_2.txt存放了两种飞行器的雷达散射截面（RCS）数据（量纲为dBsm）。请编写程序对两组数据分别计算其算术平均值，并根据该算术平均值评价两种飞行器隐身性能的好坏。

