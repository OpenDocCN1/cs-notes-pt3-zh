# # Interrupt-Driven I/O

```
copy_from_user(buffer, p, count);
enable_interrupts();
while (*printer_status_reg != READY) ;
*printer_data_register = p[0];
scheduler();
```

```
if (count == 0) {
unblock_user();
} else {
*printer_data_register = p[i];
count = count - 1;
i = i + 1;
}
acknowledge_interrupt();
return_from_interrupt();
```

(a)

(b)

Figure 5-9. Writing a string to the printer using interrupt-driven I/O.
(a) Code executed at the time the print system call is made.
(b) Interrupt service procedure for the printer.