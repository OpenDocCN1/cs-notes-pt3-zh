# # Haswell CPU

+   - 8 Total Functional Units

+   - Multiple instructions can execute in parallel

2 load, with address computation
1 store, with address computation
4 integer
2 FP multiply
1 FP add
1 FP divide

+   - Some instructions take > 1 cycle, but can be pipelined

| Instruction | Latency | Cycles/Issue |
|---|---|---|
| Load / Store | 4 | 1 |
| Integer Multiply | 3 | 1 |
| Integer/Long Divide | 3-30 | 3-30 |
| Single/Double FP Multiply | 5 | 1 |
| Single/Double FP Add | 3 | 1 |
| Single/Double FP Divide | 3-15 | 3-15 |