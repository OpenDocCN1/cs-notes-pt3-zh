# # Bounds check Shortcut

# ## Reduce an index-out-of-bounds check

If ($a1>=$t2 & $a1<0) goto IndexOutofBounds

sltu $t0, $a1, $t2 #Temp reg $t0=0 if k>=length or k<0

beq $t0, $zero, IndexOutofBounds # if bad, goto Error

lw $t2, 4($s6) #temp reg $s2=length of array save

slt $t0, $s3, $zero #temp reg $t0=1 if i<0

slt $t3, $s3, $t2 #temp reg $t3=0, if i>=length

slti $t3, $t3, 1 #temp reg $t3=1, if i>=length

or $t3, $t3, $t0 # $t3=1, if i is out of bounds

bne $t3,$zero, IndexOutofBounds # if out of bounds, goto Error