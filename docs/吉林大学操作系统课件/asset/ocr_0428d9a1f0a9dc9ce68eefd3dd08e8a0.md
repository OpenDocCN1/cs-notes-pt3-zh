# 例4-6 简单批处理

```
COBEGIN
    PROCESS reader;
        VAR card: cardimage
        LOOP
            Read card from cardreader;
            REGION ib WHEN inbuff.size<n DO
                inbuff.slots[inbuff.tail]:=card;
                inbuff.size := inbuff.size+1;
                inbuff.tail := (inbuff.tail+1) MOD n;
            ENDDO
        ENDLOOP
    ENDPROCESS
```