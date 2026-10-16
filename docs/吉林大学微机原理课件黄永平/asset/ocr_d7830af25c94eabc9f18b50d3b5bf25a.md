# 2)相等循环指令

# LOOPE / LOOPZ      disp8

;CX←CX-1;

若CX≠0 且Z=1 则IP←IP+disp8 , disp8 = -128~127

CX←循环次数

循环体

LOOPE/LOOPZ
disp8

CX←CX-1
CX≠0 and Z=1?

最多
CX次

CX = CX - 1
if (CX <> 0) and (ZF = 1) then
jump
else
no jump, continue

Y

N