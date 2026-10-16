# Recursive Bit-String Enumerator

```
procedure recEnumBitStrings(soFar,n)
{enumerate all strings consisting of soFar concatenated with a bit-string of length n}
if n=0 then begin print soFar; return end
enumBitStrings(soFar·‘0’, n−1)
enumBitStrings(soFar·‘1’, n−1)
procedure enumBitStrings(n∈N)
recEnumBitStrings(ε, n) {soFar=empty str}
```