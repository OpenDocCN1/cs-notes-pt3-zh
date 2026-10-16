# # 可控加法/减法（CAS）单元

+   - 当输入线P=0时，CAS做加法运算
+   - 当输入线P=1时，CAS做减法运算

S<sub>i</sub>=A<sub>i</sub>⊕(B<sub>i</sub>⊕P)⊕C<sub>i</sub>
C<sub>i+1</sub>=(A<sub>i</sub>+C<sub>i</sub>)(B<sub>i</sub>⊕P)+A<sub>i</sub>C<sub>i</sub>

当P=0时：
S<sub>i</sub>=A<sub>i</sub>⊕B<sub>i</sub>⊕C<sub>i</sub>
C<sub>i+1</sub>=A<sub>i</sub>B<sub>i</sub>+B<sub>i</sub>C<sub>i</sub>+A<sub>i</sub>C<sub>i</sub>

当P=1时：
S<sub>i</sub>=A<sub>i</sub>⊕B̄<sub>i</sub>⊕C<sub>i</sub>
C<sub>i+1</sub>=A<sub>i</sub>B̄<sub>i</sub>+B̄<sub>i</sub>C<sub>i</sub>+A<sub>i</sub>C<sub>i</sub>

![](bbox=[0.479, 0.323, 0.961, 0.948])