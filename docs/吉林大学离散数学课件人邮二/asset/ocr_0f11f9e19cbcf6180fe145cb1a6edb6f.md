+   (1) $P \leftarrow A$
+   (2) $k \leftarrow 1$
+   (3) $i \leftarrow 1$
+   (4) 若 $p_{ik}=1$, 对 $j=1,2,\cdots,n$ 作 $p_{ij} \leftarrow p_{ij} \lor p_{kj}$
+   (5) $i \leftarrow i+1$, 若 $i \le n$ 则转(4)
+   (6) $k \leftarrow k+1$, 若 $k \le n$ 则转到(3), 否则停止。

该算法的关键的一步是(4)，它判定如果 $p_{ik}=1$，将第$i$行和第$k$行的各对应元素作布尔和或逻辑加后送到第$i$行中去。