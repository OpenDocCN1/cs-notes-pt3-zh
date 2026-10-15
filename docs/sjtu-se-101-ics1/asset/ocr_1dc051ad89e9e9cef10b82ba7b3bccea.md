# Indexed Addressing Mode

+   - An expression for
+     - a memory address (or an array index)
+   - Most general form
+     - Imm(E_b, E_i, s)
+     - Constant "displacement" Imm: 1, 2 or 4 bytes
+     - Base register E_b: Any of 8 integer registers
+     - Index register E_i: Any, except for %esp
+     - S: Scale: 1, 2, 4, or 8