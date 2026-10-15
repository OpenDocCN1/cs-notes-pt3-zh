# Bidirectional

Format of allocated and free blocks

header

boundary tag (footer)

1 word

size

payload and padding

size

a = 1: allocated block
a = 0: free block

size: block size

payload: application data (allocated blocks only)

![](bbox=[0.15, 0.22, 0.8, 0.6])

![](bbox=[0.15, 0.75, 0.8, 0.85])