# 相关操作：

getblk(dev,blkno)  //assign a buffer for the given block

bread(dev,blkno)  //read a block(if necessary), return buf pointer

bread a(dev,blkno,rablkno)  //read in first block, like read; but also start io on second block

bwrite(bp)  //write the buffer, wait for completion, then release

bawrite(bp)  //start the io, release buffer, no wait for completion

bdwrite(bp) //release buffer, mark it so that if it is grabbed for another purpose, it will be written out before being given up

brelse(bp)  //release the buffer, with no io implied