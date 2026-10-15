# Comparing Approaches

| | ISR | SoftIRQ | Tasklet | WorkQueue | KThread |
|---|---|---|---|---|---|
| Will disable all interrupts? | Briefly | No | No | No | No |
| Will disable other instances of self? | Yes | Yes | No | No | No |
| Higher priority than regular scheduled tasks? | Yes | Yes* | Yes* | No | No |
| Will be run on same processor as ISR? | N/A | Yes | Yes | Yes | Maybe |
| More than one run can on same CPU? | No | No | No | Yes | Yes |
| Same one can run on multiple CPUs? | Yes | Yes | No | Yes | Yes |
| Full context switch? | No | No | No | Yes | Yes |
| Can sleep? (Has own kernel stack) | No | No | No | Yes | Yes |
| Can access user space? | No | No | No | No | No |

*Within limits, can be run by ksoftirqd