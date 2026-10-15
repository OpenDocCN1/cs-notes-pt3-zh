# Indirect Recursion Example

+   - Determine whether an integer is even or odd:
+   - How do we know if a number is even?
+     - we know 0 is even.
+     - we know that if n is even, then n-1 must be odd.
+   ```
+   static boolean is_even(int n)
+   {
+       if (n==0) return true;
+       else return(is_odd(n-1));
+   }
+   ```
+   - How do we know if a number is odd? It's not even!
+   ```
+   static boolean is_odd(int n)
+   {
+       return (!is_even(n));
+   }
+   ```