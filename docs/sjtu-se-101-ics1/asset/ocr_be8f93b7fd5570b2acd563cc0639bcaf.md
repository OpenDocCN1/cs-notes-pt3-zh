# Truncating Numbers

+   - Unsigned Truncating
+     $B2U_w([x_w, x_{w-1}, \cdots, x_0]) \bmod 2^k = B2U_k([x_k, x_{k-1}, \cdots x_0])$
+   - Signed Truncating
+     $B2T_k([x_k, x_{k-1}, \cdots x_0]) = U2T_k(B2U_w([x_w, x_{w-1}, \cdots, x_0]) \bmod 2^k)$