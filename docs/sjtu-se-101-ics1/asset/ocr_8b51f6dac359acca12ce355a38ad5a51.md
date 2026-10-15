# Jump Table

+   1. .section .rodata
+   2. .align 4
+   3. .L7:
+   4.     .long .L3        case 100: loc_a
+   5.     .long .L2        case 101: loc_def
+   6.     .long .L4        case 102: loc_b
+   7.     .long .L5        case 103: loc_c
+   8.     .long .L6        case 104: loc_d
+   9.     .long .L2        case 105: loc_def
+   10.    .long .L6        case 106: loc_d