# Time Hierarchy Theorem

+   - Obviously, stages 1, 2 and 3 can be performed within $O(t(n))$ time
+   - In stage 4, every time $D$ simulates one step of $M$, it takes $M$'s current state in its transition function so that it can update $M$'s tape head and looks up $M$'s next action in its transition function to update $M$'s tape appropriately.
+     - All state, tape symbol and transition function of $M$ are stored somewhere on $D$'s tape
+     - This will be very inefficient if they are stored far away from each other