# Using Vector Instructions

| Method | Integer Add | Integer Mult | Double FP Add | Double FP Mult |
|---|---:|---:|---:|---:|
| Scalar Best | 0.54 | 1.01 | 1.01 | 0.52 |
| Vector Best | 0.06 | 0.24 | 0.25 | 0.16 |
| *Latency Bound* | *0.50* | *3.00* | *3.00* | *5.00* |
| *Throughput Bound* | *0.50* | *1.00* | *1.00* | *0.50* |
| *Vec Throughput Bound* | *0.06* | *0.12* | *0.25* | *0.12* |

+   - **Make use of AVX Instructions**
+     - Parallel operations on multiple data elements
+     - See Web Aside OPT:SIMD on CS:APP web page