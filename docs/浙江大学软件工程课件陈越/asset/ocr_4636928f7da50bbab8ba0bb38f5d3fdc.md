# # 第11章 构造函数与析构函数

# ## § 11.2 构造函数

# ## 一、重载构造函数

例：class Name{
...
public:
Name();
Name(char*first);
Name(char*first,char*last);
...
};

Name name1;
Name name2("Yun ");
Name name3("Yun ",
" Zhao ");