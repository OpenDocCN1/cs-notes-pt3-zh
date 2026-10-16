# 1.5 Basic Program Execution Registers

▪ Default segment and offset combinations

| Special Purpose | Segment | 16-bit Offset | 32-bit Offset |
|---|---|---|---|
| Instruction address | CS | IP | EIP |
| Data address | DS | BX, SI, DI, an 8- or 16-bit number | EAX, EBX, ECX, EDX, ESI, EDI, an 8- or 32-bit number |
| Stack address | SS | SP or BP | ESP or EBP |
| String destination address | ES | DI | EDI for string instructions |
| General address | FS | - | No default |
|  | GS | - | No default |