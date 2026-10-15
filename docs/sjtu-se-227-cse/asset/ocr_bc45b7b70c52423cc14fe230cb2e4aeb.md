# Disk Scheduling Goals

| Request | Movement | Time |
|---|---|---|
| Seek 1 | 0 → 0 | 0t |
| Seek 2 | 0 → 5 | 5t |
| Seek 3 | 5 → 1 | 4t |
| Seek 4 | 1 → 90 | 89t |
| Seek 5 | 90 → 100 | 10t |
| Total |  | 108t |

Shortest-Seek-First

| Request | Movement | Time |
|---|---|---|
| Seek 1 | 0 → 0 | 0t |
| Seek 2 | 0 → 5 | 5t |
| Seek 3 | 5 → 90 | 85t |
| Seek 4 | 90 → 100 | 10t |
| Seek 5 | 100 → 1 | 99t |
| Total |  | 199t |

Elevator Algorithm