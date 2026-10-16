# 2.4 Assembly Language Source Code

# ▪ Using Simplified Segment Directives

◆ .MODEL

```
`.MODEL memorymodel [[, langtype]] [[, stackoption]]`
```

| Memory mode | Max. size of seg. | File type | OS | Code seg. | Data seg. |
|---|---|---|---|---|---|
| Tiny | 64KB | .com | DOS | One seg. | |
| Small | 64KB | .exe | DOS | 1 | 1 |
| Medium | 64KB | .exe | DOS | Multi. | 1 |
| Compact | 64KB | .exe | DOS | 1 | Multi. |
| Large | 64KB | .exe | DOS | Multi. | Multi. |
| Huge | >64KB | .exe | DOS | Multi. | Multi. |
| flat | 4GB | .exe(PE) | Windows | Same seg. | |