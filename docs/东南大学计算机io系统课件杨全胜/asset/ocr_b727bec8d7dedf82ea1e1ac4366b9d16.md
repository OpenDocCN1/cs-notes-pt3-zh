# 4.3 Interrupt in x86 System

# Interrupt and Exception Classification

# Exception

# Software-Generated Exceptions

+   The INTO, INT 3, and BOUND instructions permit exceptions to be generated in software.

# Machine-Check Exceptions

+   The P6 family and Pentium processors provide both internal and external machine-check mechanisms for checking the operation of the internal chip hardware and bus transactions.

+   These mechanisms are implementation dependent.

+   When a machine-check error is detected, the processor signals a machine-check exception (vector 18) and returns an error code.