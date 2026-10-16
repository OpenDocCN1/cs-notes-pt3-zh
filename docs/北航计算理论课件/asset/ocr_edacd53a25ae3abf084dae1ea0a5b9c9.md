# § 4.4 代数语义

+   - `axiom eval( var(x)) = undefined`
+     `eval ( cons(n)) = n`
+     `eval ( add( e1, e2)) = eval(e1) + eval(e2)`
+     `eval ( sub( e1, e2)) = eval(e1) - eval(e2)`
+     `eval ( mul( e1, e2)) = eval(e1) × eval(e2)`
+     `defined(e) = True }`

+   - 定理：上述的Expression是
+     - 充分完备的；
+     - 强等价、弱等价是可判定的；
+     - 层次是一致的。