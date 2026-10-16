# rules about parameter passing behavior

+   - If the marshalled parameters are local objects, they are passed by copy using a technique known as object serialization.
+     If the parameters are also remote objects, they are passed by reference.

+   - If local objects are to be passed as parameters to remote objects, they must implement the interface java.io.Serializable.