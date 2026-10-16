# DNS资源记录（RR）(3)

```
RR 格式: (name, TTL, , class, type, value)
```

| Owner name | TTL | Class | RRType | RData |
|---|---|---|---|---|
| bupt.edu.cn | 86400 | IN | NS | ns.buptnet.edu.cn |
| ns.buptnet.edu.cn | 86400 | IN | A | 202.112.10.37 |
| www.bupt.edu.cn | 86400 | IN | CNAME | vn.bupt.edu.cn |
| bupt.edu.cn | 86400 | IN | MX | mx1.bupt.edu.cn |
| www.bupt.edu.cn | 86400 | IN | A | 10.3.9.161 |

查询资源记录的命令： nslookup

```
C>nslookup –query=ns bupt.edu.cn
```