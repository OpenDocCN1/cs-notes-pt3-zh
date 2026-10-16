解：职工登记卡的类型定义如下。

```
typedef enum { male , female } sextype ;

typedef struct {
    int year, month, day ;
} datatype;

typedef struct cardperson{
    char name[8] ;        /* 姓名 */
    datatype birthdate ;  /* 出生时间 */
    sextype sex;          /* 性别 */
} typecardperson ;
```