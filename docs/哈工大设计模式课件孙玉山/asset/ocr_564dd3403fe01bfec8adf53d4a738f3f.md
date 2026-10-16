# 4. Case Study

+   - **Then call setup method in class CircularShifter setup(LineStorage lines)**
+     this method shifts the lines in “lines”, then write them into shifts_
+   - Next, the KWIC object invokes the setup method of the CircularShifter instance.
+   - The single argument for this method is LineStorage holding the lines. The CircularShifter object iterates through all lines in the LineStorage and produces circular shifts of these lines and write them into shifts_:
+     
+     shifts_ = new LineStorage();