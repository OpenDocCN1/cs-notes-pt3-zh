# Computing a Canonical Cover

+   - R = (A, B, C)
+   F = {A → BC
+   B → C
+   A → B
+   AB → C}

Combine A → BC and A → B into A → BC

Set is now {A → BC, B → C, AB → C}

+   - A is extraneous in AB → C
+   
+   • Check if the result of deleting A from AB → C is implied by the other dependencies
+   
+   › Yes: in fact, B → C is already present!
+   
+   • Set is now {A → BC, B → C}

+   - C is extraneous in A → BC
+   
+   • Check if A → C is logically implied by A → B and the other dependencies
+   
+   › Yes: using transitivity on A → B and B → C.
+   
+   - Can use attribute closure of A in more complex cases

+   - The canonical cover is:
+   
+   A → B
+   
+   B → C