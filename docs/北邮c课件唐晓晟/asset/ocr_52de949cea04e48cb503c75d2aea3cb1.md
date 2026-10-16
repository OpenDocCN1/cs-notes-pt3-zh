# 4.3 字符类型

+   - 类型为char的变量可以保存具体实现所用的字符集里面的一个字符
+   - 常用字符类型都至少包括8bit,可以保存出256种不同的数值
+   - 字符集一般都采用ISO-646的某个变形,比如说ASCII(ANSI3.4-1968)

# 以下假设都是不安全的

+   - 8位字符集中共有不超过127个字符(有的字符集提供了255个字符)
+   - 不存在超出英语的字符(大部分欧洲语言提供更多的字符)
+   - 字符序列是连续排列的(EBCDIC在“和”和“”之间留有空隙)
+   - 写C++所需要的每个字符都是可用的(有些国家的字符集中没有提供{}和[]，C++提供的解决方法有关键字、二联符和三联符)

# 解决受限的字符集

| 关键字(keywords) C++ | 二联符(digraph) C++ | 三联符(trigraph) C |
|---|---|---|
| and | && | <% | ??= | # |
| and_eq | &= | %> | ??( | [ |
| bitand | & | <: | ??/ | \ |
| bitor | | | >= | ??< | { |
| compl | ~ | :> | ??! | | |
| not | ! | %: | ??) | ] |
| or | || | %:%: | ??> | } |
| or_eq | |= | | ??/ | ^ |
| xor | ^ | | ??! | | |
| xor_eq | ^= | | ??! | | |
| not_eq | != | | ??- | ~ |

# digraph and trigraph Examples

```
例II C++ trigraph
#include <stdio.h>
void main(int argc, char *argv?(?)?)
{?
    if (argc-1 && argv?(?)(?)? != NULL)
        printf("Hello, %s!\n",argv?(?)?);
    else printf("Hello, world!\n");
    return 0;
}%
```

```
例I C++ digraph
#include <stdio.h>
main(int argc, char *argv<:>)
<%
    if (argc-1 and argv<:>0<:> != NULL)
        printf("Hello, %s!\n",argv<:>1<:>);
    else
        printf("Hello, world!\n");
    return 0;
%>%
```