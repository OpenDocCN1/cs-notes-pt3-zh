# 使用非标准的分隔符

```
int main()
{
    Punct_stream ps(cin);
    ps.whitespace(";,:.? !\"{}<>\/&$@#%^*|~"); // note \" means " in string
    ps.case_sensitive(false);

    cout << "please enter words\n";
    vector<string> vs;
    string word;
    while (ps>>word) vs.push_back(word);  // read words

    sort(vs.begin(),vs.end());        // sort in lexicographical order
    for (int i=0; i<vs.size(); ++i)    // write dictionary
        if (i==0 || vs[i]!=vs[i-1]) cout << vs[i] << endl;
}
```