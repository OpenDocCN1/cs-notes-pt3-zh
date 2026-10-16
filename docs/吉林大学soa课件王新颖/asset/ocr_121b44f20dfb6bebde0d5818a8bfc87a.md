# Example: Counter class

+   - For the sake of example, we will create and test a trivial “counter” class
+     - The constructor will create a counter and set it to zero
+     - The increment method will add one to the counter and return the new value
+     - The decrement method will subtract one from the counter and return the new value
+   - We write the test methods before we write the code
+     - This has the advantages described earlier
+     - Depending on the JUnit tool we use, we may have to create the class first, and we may have to populate it with stubs (methods with empty bodies)
+   - Don’t be alarmed if, in this simple example, the JUnit tests are more code than the class itself