# The Problem of Parsing

+   - On last course, I noted that the rules for forming an expression can be expressed in the form of a **grammar**, as follows:
+   
+     E → constant
+     E → identifier
+     E → E op E
+     E → ( E )
+   - The process of translating an expression from a string to its internal form is called **parsing**.