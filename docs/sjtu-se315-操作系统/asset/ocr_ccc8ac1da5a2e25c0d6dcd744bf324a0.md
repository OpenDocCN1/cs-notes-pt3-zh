# Deadlock Pitfalls in Reality

Even **deadlock-free** code would deadlock once deployed

Due to dependencies on deadlock-prone third party libraries or runtimes

Examples: web browsers plug-ins, Java beans.

Upgrade of such libraries/runtimes can introduce new deadlocks during execution.