# Sniffer Portable - Local, Ethernet (Line Speed at 100 Mbps) - [Sniffer? Decode v? Ethernet Frames]

| No. | Status | Source Address | Dest Address | Summary | Len (B) | Rel Time | Delta Time |
|---|---|---|---|---|---:|---:|---:|
| 1 | X | [202.118.236.152] | hit01.hit.edu.cn | DNS: Q ID=17525 QP=QUERY NAME=www.hit.edu.cn | 162 | 0:00:00.000 | 0.000 |
| 2 |  | hit01.hit.edu.cn | [202.118.236.152] | DNS: R ID=17525 OP=QUERY STAT=OK NAME=www.hit.edu.cn | 162 | 0:00:00.000 | 0.000 |

```
DNS:  ZONE Section
    Name = www.hit.edu.cn
    Type = Host address (A,1)
    Class = Internet (IN,1)

DNS:  Answer section:
    Name = www.hit.edu.cn
    Type = Host address (A,1)
    Class = Internet (IN,1)
    Time-to-live = 3600 (seconds)
    Length = 4
    Address = [202.118.224.25]

DNS:  Authority section 1:
    Name = hit.edu.cn
    Type = Authoritative name server (NS,2)
    Class = Internet (IN,1)
    Time-to-live = 86400 (seconds)
    Length = 8
    Name server domain name = hit02.hit.edu.cn

DNS:  Authority section 2:
    Name = hit.edu.cn
    Type = Authoritative name server (NS,2)
    Class = Internet (IN,1)
    Time-to-live = 86400 (seconds)
    Length = 8
    Name server domain name = hit01.hit.edu.cn

DNS:  Additional record section 1:
```

```
00000000  00 e0 4c 3d 27 ba 00 b2 b3 bc 2f ea 08 00 45 00
00000010  94 00 00 40 00 30 11 da ce ca 76 e0 64 ca 76  ...
00000020  00 00 00 00 00 00 00 00 4f 75 65 80 01 00  ...
00000030  00 01 00 02 00 00 00 77 77 77 2e 68 69 74 2e
00000040  74 75 2e 63 6e 00 00 01 00 01 00 00 01 00  ...
```