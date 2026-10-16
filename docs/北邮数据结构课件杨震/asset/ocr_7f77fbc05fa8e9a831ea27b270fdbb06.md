```
TYPE blkptr=^blk;
    blk=RECORD
        header:RECORD
            llink,rllink:blkptr;
            tag:0..1;
            size:integer
        END;
            space:ARRAY[1..size-2] OF
datatype;
        footer:RECORD
            uplink:blkptr;
            tag:0..1
        END
END;
```