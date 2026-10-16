# 平面几何投影变换——斜投影图

x'_q = z_q ctg α cos β + x_q

y'_q = z_q ctg α sin β + y_q

斜平行投影的投影变换矩阵为：

T = [ 1 0 0 0 ; 0 1 0 0 ; ctg α cos β ctg α sin β 0 0 ; 0 0 0 1 ]