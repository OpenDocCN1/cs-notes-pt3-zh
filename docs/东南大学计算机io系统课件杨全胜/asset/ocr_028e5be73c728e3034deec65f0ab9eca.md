# 7.4 16550 UART

# Interrupt Enable Register(IER)

DLAB=0, A2A1A0=001

| D7 | D6 | D5 | D4 | D3 | D2 | D1 | D0 |
| 0 | 0 |  |  | I0E | I3E | I1E | I2E |

1=enables the MODEM Status Interrupt

1=enables the THR Empty Interrupt

1=enables the Receiver Line Status Interrupt

1=enables the Received Data Available Interrupt