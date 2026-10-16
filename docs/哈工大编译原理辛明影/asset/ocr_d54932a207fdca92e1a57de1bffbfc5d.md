# 此时参数是左结合还是右结合？

Elist → E
{初始化queue，然后将E.addr加入到queue的队尾}

Elist → Elist, E
{将E.addr添加到queue的队尾}

S → call id (Elist)
{ n :=0;
repeat n:=n+1; 从queue的队首取出一个实参地址p;
gencode('param', -, -, p);
until queue为空;
gencode('call', id.addr, n, -)}

S → return E{if 需要返回结果 then
gencode(':=', E.addr, -, F);
gencode('ret', -, -, -)}