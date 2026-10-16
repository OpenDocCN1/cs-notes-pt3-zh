# 5.2 Structure and pins of 8254

# Operation and Command

I/O port address: four port (address use A1A0);

Command: initial—set mode, write initial count operation—rewrite initial count, command to read status

Status: current count, mode and current state

Initial count N = f_CLKi / f_OUTi