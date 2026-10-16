# 4.1 数组

```
int intArray2[][] = new int[3][];
intArray2[0] = new int[3];
intArray2[1] = new int[4];
intArray2[2] = new int[5];

intArray2[0][0] = 1;
intArray2[0][1] = 2;
intArray2[0][2] = 3;

intArray2[1][0] = 4;
intArray2[1][1] = 5;
intArray2[1][2] = 6;
intArray2[1][3] = 7;

intArray2[2][0] = 8;
intArray2[2][1] = 9;
intArray2[2][2] = 10;
intArray2[2][3] = 11;
intArray2[2][4] = 12;

for(int i=0; i<intArray2.length; i++) {
    for(int j=0; j<intArray2[i].length; j++) {
        System.out.print(intArray2[i][j] + " ");
    }
    System.out.print("\n");
}
```

| 1 | 2 | 3 |  |  |
|---|---|---|---|---|
| 4 | 5 | 6 | 7 |  |
| 8 | 9 | 10 | 11 | 12 |

![](bbox=[0.84, 0.03, 0.98, 0.16])