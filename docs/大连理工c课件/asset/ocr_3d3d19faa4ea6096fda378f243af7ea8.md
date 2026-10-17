# # 第7章 模板

# ## 7.3 类模板

类模板由模板说明和类说明构成

template <类型形式参数表> 类声明

template< typename Type > class TClass { // TClass的成员函数 private : Type DateMember ; //... };

类属参数必须至少在类说明中出现一次

例如