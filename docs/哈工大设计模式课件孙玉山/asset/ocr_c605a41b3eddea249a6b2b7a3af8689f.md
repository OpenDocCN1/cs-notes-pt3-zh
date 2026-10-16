# 2. Case Studies

+   - **Problems:**
+     - the layered architecture does not fit actual data and control flow patterns.
+     - The layers suggest that services and requests are passed between adjacent components. Actually, information passing is less straightforward.
+     - **Example:**
+       - data requiring fast response may be sent directly from sensor to level 7 to deal with the problem.
+       - the corresponding commands may have to skip levels to reach the motors in time.