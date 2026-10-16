# 3. 2驱动程序的实现

[1]初始化： Stack := empty ; Push(#); Push(S); 即由符号栈和输入流构成的初始格局为： (#S, a₁a₂...aₙ#)

[2] 读第一个输入符： Read(a);

[3] 若当前格局是(#,#)，则成功结束；否则转下一步；

[4] 设当前格局为(.... X, a....)，则：

+   - 若X∈ V_T & X=a ，则：
+     { Pop(1); Read(a); goto [3] }

+   - 若X∈ V_T & X≠ a ，则 Error;

+   - 若X ∈ V_N ，则：
+     if T(X, a)=X→Y₁ Y₂...... Yₙ
+     then { Pop(1); Push(Yₙ,...,Y₁); goto[3] }
+     else Error