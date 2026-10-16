动作文法为：
♦ ProcFunDec → ProcDec | FunDec
ProcDec →
Procedure id (ParamList) ; Declaration #Entry# ProgramBody #EndProc#
♦ FunDec →
Function id (ParamList) : Type; Declaration #Entry# ProgramBody #EndFunc#
♦ Entry:
给子程序Q分配新标号LabelQ，并将它填到Q的符号表项中；产生入口中间代码：
( ENTRY , LabelQ , SizeQ , LevelQ ) 或 (ENTRY, Q, –, –)
♦ EndProc和EndFunc:
产生出口中间代码：
( ENDPROC , — , — , — )
或 ( ENDFUNC , — , — , — )