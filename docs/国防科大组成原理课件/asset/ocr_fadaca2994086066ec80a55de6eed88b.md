# OpenMP共享存储编程标准

+   - OpenMP Architecture Review Board牵头提出
+     - 最初形成于1997年，2002年OpenMP2.0，2008年OpenMP3.0、2013年OpenMP4.0
+   - 主要API（Application Program Interface）包含
+     - 制导指令、运行库和环境变量
+     - 针对基本编程语言（C、C++和Fortran）进行编译制导扩展，用注释符“#”符开始，不支持OpenMP的编译器中可以忽略，支持OpenMP的编译器才有用
+   - 由于GCC的支持，主流处理器都支持OpenMP编译器
+     - 如Intel、AMD、IBM、龙芯等