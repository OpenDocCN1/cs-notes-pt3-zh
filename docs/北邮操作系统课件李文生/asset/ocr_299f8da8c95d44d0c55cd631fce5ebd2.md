# 12.2 Disk Structure

![](bbox=[0.04, 0.22, 0.27, 0.62])

+   - Disk drives are addressed as large 1-dimensional arrays of logical blocks, where the logical block is the smallest unit of transfer. (block size is usually 512 bytes)
+   - The 1-dimensional array of logical blocks is mapped into the sectors of the disk sequentially.
+     - Sector 0 is the first sector of the first track on the outermost cylinder.
+     - Mapping proceeds in order through that track, then the rest of the tracks in that cylinder, and then through the rest of the cylinders from outermost to innermost.
+   - Constant Linear Velocity (常数线性周转率)
+     - 位密度相同, CD-ROM, DVD-ROM
+   - Constant Angular Velocity (常数角周转率)
+     - 位密度不同, hard disk

![](bbox=[0.03, 0.68, 0.28, 0.96])