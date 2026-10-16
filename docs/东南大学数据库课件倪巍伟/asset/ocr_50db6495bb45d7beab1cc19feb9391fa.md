【例10-1】设 F = {AB→C，D→EG，C→A，BE→C，BC→D，CG→BD，ACD→B，CE→AG}，试用算法10-1计算 (BD)⁺。

解：令 X⁽⁰⁾ = BD。

找左部为BD的子集的函数依赖，只有D→EG。X⁽¹⁾ = BD ∪ EG = BDEG，找左部为BDEG的子集的函数依赖，有D→EG，BE→C。X⁽²⁾ = BDEG ∪ EGC = BCDEG

找左部为BCDEG的子集的函数依赖，有D→EG，C→A，BE→C，BC→D，CG→BD，CE→AG。X⁽³⁾ = BCDEG ∪ ABCDEG = ABCDEG