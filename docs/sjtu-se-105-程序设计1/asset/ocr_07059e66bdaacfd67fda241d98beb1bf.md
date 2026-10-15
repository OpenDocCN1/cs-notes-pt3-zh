# 简化输入循环

```
void fill_vector(istream& ist, vector<int>& v, char terminator)
{
    // read integers from ist into v until we reach eof() or terminator
    int i = 0;
    while (ist >> i) v.push_back(i);
    if (ist.eof()) return;      // fine: we found the end of file

    // not good() and not bad() and not eof(), ist must be fail()
    ist.clear();                // clear stream state
    char c;
    ist>>c;                     // read a character, hopefully terminator
    if (c != terminator) {      // ouch: not the terminator, so we must fail
        ist.unget();            // maybe my caller can use that character
        ist.clear(ios_base::failbit); // set the state back to fail()
    }
}
```