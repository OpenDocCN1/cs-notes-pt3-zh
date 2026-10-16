# 数据的类型

+   - 数据为什么要区分类型?
+     - Untyped Perl.

Demo 2: A simple perl example

```
1 #!/usr/bin/perl
2 my $var = 1, $var1, $var2;
3 $var = $var + 2.3;
4 print $var,"\n";
5 
6 $var1 = $var,"abc";
7 print $var1,"\n";
8 $var2 = $var1+"abc";
9 print $var2,"\n";
```