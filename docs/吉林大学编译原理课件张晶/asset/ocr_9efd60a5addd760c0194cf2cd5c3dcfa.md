# GenCode(ω)的主要工作

(1)若Sem[top-1].typ ≠ Sem[top].typ ，
且Sem [top-1].typ = integer，则ω运算结果类型确定为real型，并且为左分量产生类型转换代码；
(FLOAT, [top-1].FORM,-, tempArg)

(2) 若Sem[top-1].typ ≠ Sem[top].typ ，
且Sem[top].typ = integer，则ω结果运算类型确定为real型，并且为右分量产生类型转换代码；
(FLOAT, [top].FORM,-, tempArg)

(3) 若Sem[top-1].typ = Sem[top].typ ，则ω运算结果类型确定为Sem[top-1].typ ，不产生类型转换代码；