# SQL/XML

+   - New standard SQL extension that allows creation of nested XML output
+     - Each output tuple is mapped to an XML element row

```
```xml
<university>
    <department>
        <row>
            <dept name> Comp. Sci. </dept name>
            <building> Taylor </building>
            <budget> 100000 </budget>
        </row>
        ... more rows if there are more output tuples ...
    </department>
    ... other relations ..
</university>
```
```