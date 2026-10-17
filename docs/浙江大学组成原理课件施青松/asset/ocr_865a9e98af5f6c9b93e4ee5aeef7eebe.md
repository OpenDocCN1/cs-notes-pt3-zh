# # How Exceptions Are Handled

+   - Design
+     - add a register: exception program counter(EPC)
+       save the address of the offending instruction
+     - add a status register: cause register( CauseReg)
+       hold a field that indicates the reason for the exception.
+       \(\text{bit0} = \begin{cases} \text{0 undefined instruction} \\ \text{1 overflow} \end{cases}\)
+     - Another method is to use vector interrupts

| Exception type | vector address |
|---|---|
| undefine instr | c0 00 00 00<sub>H</sub> |
| overflow | c0 00 00 20<sub>H</sub> |