# # 打印100以内素数

开始
for (i=2;i<=100;i++)
prime(i)?
打印 i
结束

prime(i)
flag = true
for (j=i/2;j>=2;j--)
i%j == 0
flag = false
return flag