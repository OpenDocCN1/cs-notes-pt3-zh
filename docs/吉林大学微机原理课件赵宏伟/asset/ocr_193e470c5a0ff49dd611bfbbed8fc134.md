+   - OUT 0BH, AL ; 对通道3设置方式，同通道1
+   - MOV AL, 0 ; 命令字
+   - OUT 08H, AL ; 对8237A设控制命令，DACK为低电平有效，
+   - ; DREQ为高电平有效，固定优先级，启动工作
+   - OUT 0AH, AL ; 使通道0去除屏蔽
+   - INC AL
+   - OUT 0AH, AL ; 使通道1去除屏蔽
+   - INC AL ;
+   - OUT 0AH, AL , 使通道2去除屏蔽
+   - INC AL ;
+   - OUT 0AH, AL ; 使通道3去除屏蔽