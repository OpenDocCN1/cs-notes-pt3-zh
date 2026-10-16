# Chapter 7 Runtime Environments

# Section 2 Storage allocation strategies

# 4. Stack allocation

# 2) Calling sequences

Steps: (1) The caller evaluates actual parameters.

+   (2) The caller stores a return address and the old value of top-sp into the callee’s activation record.

+   (3) The callee saves register values and other status information

+   (4) the callee initializes its local data and begins execution.