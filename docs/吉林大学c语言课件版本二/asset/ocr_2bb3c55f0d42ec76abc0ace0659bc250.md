# 例11-1 一个人的自然情况表
卫星数据类型

```
enum sext { male , female };
struct date {
    int year ,  month ,  day ;
};
struct preson {
    char name[10] ;
    int  age ;
    enum sext sex ;
    struct date birthdate ;
};
```

```
struct mansatellite {
    char name[10] ;
    struct date
        lounchdate ;
    float weight,
        diameter,
        orbitrad,
        angle ;
};
```