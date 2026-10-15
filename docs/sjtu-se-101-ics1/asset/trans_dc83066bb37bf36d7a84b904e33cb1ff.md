

## 位置无关代码 (PIC)

| 地址 | 条目 | 内容 | 描述 |
|---|---|---|---|
| 08049674 | GOT[0] | 0804969c | .dynamic 节的地址 |
| 08049678 | GOT[1] | 4000a9f8 | 链接器的标识信息 |
| 0804967c | GOT[2] | 4000596f | 动态链接器的入口点 |
| 08049680 | GOT[3] | 0804845a | PLT[1] (printf) 中 pushl 的地址 |
| 08049684 | GOT[4] | 0804846a | PLT[2] (addvec) 中 pushl 的地址 |

```
PLT[2] <addvec>
8048464: ff 25 84 96 04 08 jmp *0x8049684 # jump to *GOT[4]
804846a: 68 08 00 00 00 pushl $0x8 # ID for addvec
804846f: e9 d0 ff ff ff jmp 8048444 # jmp to PLT[0]
```

- 调用 addvec

```
80485bb: e8 a4 fe ff ff call 8048464 <addvec>
```

- PLT

```
PLT[0]
08048444: ff 35 78 96 04 08    pushl 0x8049678    # push &GOT[1]
80484a:  ff 25 7c 96 04 08    jmp *0x804967c    # jmp to *GOT[2] (linker)
8048450: 00 00                    # padding
8048452: 00 00                    # padding
```

```
PLT[1] <printf>
8048454: ff 25 80 96 04 08    jmp    *0x8049680    # jmp to *GOT[3]
804845a: 68 00 00 00 00    pushl $0x0    # ID for printf
804845f: e9 e0 ff ff ff    jmp    8048444    # jmp to PLT[0]
```

```
PLT[2] <addvec>
8048464: ff 25 84 96 04 08    jmp    *0x8049684    # jump to *GOT[4]
804846a: 68 08 00 00 00    pushl $0x8    # ID for addvec
804846f: e9 d0 ff ff ff    jmp    8048444    # jmp to PLT[0]
```

- 调用 addvec

```
80485bb: e8 a4 fe ff ff    call 8048464 <addvec>
```

