PROCEDURE average;
* 最多输入 N 个值(以 -999 为输入结束标志)，计算位于给定范围内的那些值
(称为有效输入值)的平均值，以及输入值的个数和有效值的个数 *
INTERFACE RETURNS average,total, input,total, valid;
INTERFACE ACCEPTS n,value,minimum,maximum;
TYPE value[1, n ] IS SCALAR ARRAY;
TYPE average,total, input,total, valid,minimum,maximum.sum IS SCALAR;
TYPE N,n,i IS INTEGER;
i=1;
total. input= total. valid=0;
sum=0
DO WHILE value[i]< > -999 and total. input<n
total. input 加 1;
IF value[i]>= minimum AND value[ i ]<=maximum
THEN
total. valid 加 1;
sum=sum+value[ i ];
ELSE skip
END IF;
i 加 1;
END DO;
IF total. valid>0
THEN average= sum/total. valid;
ELSE average= - 999;
END IF
END average