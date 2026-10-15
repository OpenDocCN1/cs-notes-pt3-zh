```
bool Punct_stream::is_whitespace(char c)
{
    for (int i = 0; i<white.size(); ++i) if (c==white[i]) return true;
    return false;
}
```

```
Punct_stream::operator bool()
{
    return !(source.fail() || source.bad()) && source.good();
}
```