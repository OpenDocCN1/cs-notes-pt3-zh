# Fig 9.20 Sharing of Segments

![](bbox=[0.132, 0.153, 0.887, 0.92])

Logical memory process P₁

segment 0: editor

segment 1: data 1

| limit | base |
|---:|---:|
| 25286 | 43062 |
| 4425 | 68348 |

segment table process P₁

Logical memory process P₂

segment 0: editor

segment 1: data 2

| limit | base |
|---:|---:|
| 25286 | 43062 |
| 8850 | 90003 |

segment table process P₂

Physical memory

43062

68348

72773

90003

98553