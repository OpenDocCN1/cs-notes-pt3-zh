# 例：

+   - out[B] = gen[B] ∪ ( in[B] − kill[B] )
+   - in[B]为进入基本块时的数据流信息
+   - kill[B] = kill[d1] ∪ kill[d2]...∪ kill[dn]，d1~dn依次为基本块中的语句
+   - gen[B] = gen[dn] ∪(gen[d(n-1)] − kill[dn]) ∪(gen[d(n-2)] − kill[d(n-1)] − ... − kill[dn])...∪(gen[d1] - kill[d2] - kill[d3]...- kill[dn])

d1: a = b + 1

d2: a = b + 2

kill[B] = kill[d1] ∪ kill[d2] = {d2} ∪ {d1} = {d1, d2}

gen[B] = gen[d2] ∪ (gen[d1] − kill[d2]) = {d2} ∪ ({d1} − {d1}) = {d2}

out[B] = gen[B] ∪ ( in[B] − kill[B] ) = {d2} ∪ (in[B] - {d1, d2})