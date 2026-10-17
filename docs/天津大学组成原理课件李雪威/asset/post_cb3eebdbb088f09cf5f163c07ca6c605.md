

## Effect of Separate Accumulators

| Method | Integer Add | Integer Mult | Double FP Add | Double FP Mult |
|---|---:|---:|---:|---:|
| Combine4 | 1.27 | 3.01 | 3.01 | 5.01 |
| Unroll 2x1 | 1.01 | 3.01 | 3.01 | 5.01 |
| Unroll 2x1a | 1.01 | 1.51 | 1.51 | 2.51 |
| Unroll 2x2 | 0.81 | 1.51 | 1.51 | 2.51 |
| Latency Bound | 1.00 | 3.00 | 3.00 | 5.00 |
| Throughput Bound | 0.50 | 1.00 | 1.00 | 0.50 |

- Int + makes use of two load units
  ```text
  x0 = x0 OP d[i];
  x1 = x1 OP d[i+1];
  ```
- 2x speedup (over unroll2) for Int *, FP +, FP *

## Separate Accumulators

```text
x0 = x0 OP d[i];
x1 = x1 OP d[i+1];
```

![](img/be2cf0737cec89669e7b18813ea2d3b7_477_0.png)

- **What changed:**
  - Two independent “streams” of operations

- **Overall Performance**
  - N elements, D cycles latency/op
  - Should be (N/2+1)*D cycles:  
    **CPE = D/2**
  - CPE matches prediction!

*What Now?*

## Unrolling & Accumulating

### Idea

- Can unroll to any degree L
- Can accumulate K results in parallel
- L must be multiple of K

### Limitations

- Diminishing returns
  - Cannot go beyond throughput limitations of execution units
- Large overhead for short lengths
  - Finish off iterations sequentially

## Unrolling & Accumulating: Double *

- **Case**
  - Intel Haswell
  - Double FP Multiplication
  - Latency bound: 5.00. Throughput bound: 0.50

| FP * | 1 | 2 | 3 | 4 | 6 | 8 | 10 | 12 |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| 1 | 5.01 | 5.01 | 5.01 | 5.01 | 5.01 | 5.01 | 5.01 | |
| 2 | | 2.51 | | 2.51 | | 2.51 | | |
| 3 | | | 1.67 | | | | | |
| 4 | | | | 1.25 | | 1.26 | | |
| 6 | | | | | 0.84 | | | 0.88 |
| 8 | | | | | | 0.63 | | |
| 10 | | | | | | | 0.51 | |
| 12 | | | | | | | | 0.52 |

## Unrolling & Accumulating: Int +

### Case

- Intel Haswell
- Integer addition
- Latency bound: 1.00. Throughput bound: 0.50

| FP * | \multicolumn{8}{c}{Unrolling Factor L} |
|---|---|---|---|---|---|---|---|---|
| K | 1 | 2 | 3 | 4 | 6 | 8 | 10 | 12 |
| 1 | 1.27 | 1.01 | 1.01 | 1.01 | 1.01 | 1.01 | 1.01 | |
| 2 | | 0.81 | | 0.69 | | 0.54 | | |
| 3 | | | 0.74 | | | | | |
| 4 | | | | 0.69 | | 1.24 | | |
| 6 | | | | | 0.56 | | | 0.56 |
| 8 | | | | | | 0.54 | | |
| 10 | | | | | | | 0.54 | |
| 12 | | | | | | | | 0.56 |

## Achievable Performance

| Method | Integer Add | Integer Mult | Double FP Add | Double FP Mult |
|---|---:|---:|---:|---:|
| Best | 0.54 | 1.01 | 1.01 | 0.52 |
| Latency Bound | 1.00 | 3.00 | 3.00 | 5.00 |
| Throughput Bound | 0.50 | 1.00 | 1.00 | 0.50 |

- Limited only by throughput of functional units
- Up to 42X improvement over original, unoptimized code

## Programming with AVX2

### YMM Registers

- 16 total, each 32 bytes
- 32 single-byte integers

![](img/be2cf0737cec89669e7b18813ea2d3b7_482_0.png)

- 16 16-bit integers

![](img/be2cf0737cec89669e7b18813ea2d3b7_482_1.png)

- 8 32-bit integers

![](img/be2cf0737cec89669e7b18813ea2d3b7_482_2.png)

- 8 single-precision floats

![](img/be2cf0737cec89669e7b18813ea2d3b7_482_3.png)

- 4 double-precision floats

![](img/be2cf0737cec89669e7b18813ea2d3b7_482_4.png)

- 1 single-precision float

![](img/be2cf0737cec89669e7b18813ea2d3b7_482_5.png)

- 1 double-precision float

![](img/be2cf0737cec89669e7b18813ea2d3b7_482_6.png)

## SIMD Operations

- SIMD Operations: Single Precision

```
vaddpsd %ymm0, %ymm1, %ymm1
```

![](img/be2cf0737cec89669e7b18813ea2d3b7_483_0.png)

- SIMD Operations: Double Precision

```
vaddpd %ymm0, %ymm1, %ymm1
```

![](img/be2cf0737cec89669e7b18813ea2d3b7_483_1.png)

## Using Vector Instructions

| Method | Integer Add | Integer Mult | Double FP Add | Double FP Mult |
|---|---:|---:|---:|---:|
| Scalar Best | 0.54 | 1.01 | 1.01 | 0.52 |
| Vector Best | 0.06 | 0.24 | 0.25 | 0.16 |
| *Latency Bound* | *0.50* | *3.00* | *3.00* | *5.00* |
| *Throughput Bound* | *0.50* | *1.00* | *1.00* | *0.50* |
| *Vec Throughput Bound* | *0.06* | *0.12* | *0.25* | *0.12* |

- **Make use of AVX Instructions**
  - Parallel operations on multiple data elements
  - See Web Aside OPT:SIMD on CS:APP web page

