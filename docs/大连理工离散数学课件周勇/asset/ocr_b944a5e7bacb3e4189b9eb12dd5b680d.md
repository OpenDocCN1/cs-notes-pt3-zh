# 谓词逻辑求解实际问题

第三步，证明

+   (1) ¬(∀x)(YJS(x) → CJYX(x))　　　　　　　　　　　　　　　　　P
+   
+   (2) (∃x)¬(¬YJS(x) ∨ CJYX(x))　　　　　　　　　　　　　　　　T，(1)
+   
+   (3) YJS(a) ∧ ¬CJYX(a)　　　　　　　　　　　　　　　　　　　　ES，(2)
+   
+   (4) YJS(a)　　　　　　　　　　　　　　　　　　　　　　　　　T，(3)
+   
+   (5) ¬CJYX(a)　　　　　　　　　　　　　　　　　　　　　　　　T，(3)
+   
+   (6) (∀x)(YJS(x) → (CJKS(x) ∨ MKS(x)))　　　　　　　　　　　　P
+   
+   (7) YJS(a) → (CJKS(a) ∨ MKS(a))　　　　　　　　　　　　　　　US，(6)
+   
+   (8) CJKS(a) ∨ MKS(a)　　　　　　　　　　　　　　　　　　　　T，(4)，(7)
+   
+   (9) (∀x)((YJS(x) → (MKS(x) ↔ CJYX(x))))　　　　　　　　　　　P