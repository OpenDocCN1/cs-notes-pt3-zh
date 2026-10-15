# Issues with ext3

disks usually have write caches and re-order writes, for performance

sometimes hard to turn off (the disk lies)

often with re-ordering enabled for speed, out of ignorance

bad news if disk writes commit block before preceding stuff

then recovery replays "descriptors" with random block #s!

and writes them with random content!

how to solve this problem?

using checksum