
## 文本 vs.二进制文件

+   - 在使用文本文件时，我们可以
+     - 读文本 (不需要复杂的程序)
+     - 可以更加容易地调试程序
+     - 文本可以在不同的系统之间移植
+     - 大部分信息可以用文本来表示
+   - 在下列情况下必须使用二进制文件
+     - 例如，图像文件、声音文件

## 二进制文件

```cpp
int main()
// use binary input and output
{
    cout << "Please enter input file name\\n";
    string name;
    cin >> name;
    ifstream ifs(name.c_str(),ios_base::binary);        // note: binary
    if (!ifs) error("can't open input file ", name);

    cout << "Please enter output file name\\n";
    cin >> name;
    ofstream ofs(name.c_str(),ios_base::binary);        // note: binary
    if (!ofs) error("can't open output file ", name);

    // “binary” tells the stream not to try anything clever with the bytes
}
```

![](img/d2d3f908f0e1c0f8ca98d9dfbe006a9f_477_0.png)

```
fstream fs(name.c_str());    // open for input and output
// ...
fs.seekg(5);    // move reading position ('g' for 'get') to 5 (the 6th character)
char ch;
fs>>ch;    // read and increment reading position
cout << "character[6] is " << ch << '(' << int(ch) << ")\n";
fs.seekp(1);    // move writing position ('p' for 'put') to 1 (the 2nd character)
fs<<'y';    // write and increment writing position
```

+   - 无论何时，你都可以
+     - 使用简单的流机制
+       - 流/流机制是非常重要的概念
+       - 在你的大部分代码中都是用“普通的”istream 和ostream来编码
+     - 定位非常容易出错
+       - 对文件结尾位置的处理是与系统相关的，并且基本上不受检查

## 字符串流

+   - 非常有用
+     - 格式化固定尺寸的空间 (例如图形化界面 GUI)
+     - 从字符串中抽取具有类型的对象

## 类型 vs. 行

+   - 读一个字符串

```
string name;
cin >> name;        // input: Dennis Ritchie
cout << name << '\n';  // output: Dennis
```

+   - 读一行

```
string name;
getline(cin,name);       // input: Dennis Ritchie
cout << name << '\n';    // output: Dennis Ritchie
// now what?
// maybe:
istringstream ss(name);
ss>>first_name;
ss>>second_name;
```

## 字符

+   - 我们也可以读入单个字符

```
char ch;
while (cin>>ch) {    // read into ch, skipping whitespace characters
    if (isalpha(ch)) {
        // do something
    }
}
```

```
while (cin.get(ch)) { // read into ch, don't skip whitespace characters
    if (isspace(ch)) {
        // do something
    }
    else if (isalpha(ch)) {
        // do something else
    }
}
```

## 字符

• 如果使用字符输入，经常需要使用下面的函数（在头文件 `<ctype>` 中）：

+   - `isspace(c)` — *is c whitespace? (' ', '\t', '\n', etc.)*  
+   - `isalpha(c)` — *is c a letter? ('a'..'z', 'A'..'Z') note: not '_'*  
+   - `isdigit(c)` — *is c a decimal digit? ('0'..'9')*  
+   - `isupper(c)` — *is c an upper case letter?*  
+   - `islower(c)` — *is c a lower case letter?*  
+   - `isalnum(c)` — *is c a letter or a decimal digit?*

+   - 读入下面的行
+     - As planned, the guests arrived; then,
+     - 会得到
+       As
+       planned,
+       the
+       guests
+       arrived;
+       then,
+     - 实际上我们希望得到
+       As
+       planned
+       the
+       guests
+       arrived
+       then

## 使用非标准的分隔符

```
string line;
getline(cin,line);      // read into line
for (int i=0; i<line.size(); ++i) // replace each punctuation character by a space
    switch(line[i]) {
    case ',': case '.': case ';': case '?': case '!':
        line[i] = ' ';
    }

stringstream ss(line);    // make an istream ss reading from line
vector<string> vs;
string word;
while (ss>>word)          // read words without punctuation characters
    vs.push_back(word);
```

## 使用非标准的分隔符

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

```
class Punct_stream { // like an istream, but the user can add to
    // the set of whitespace characters
public:
    Punct_stream(istream& is) : source(is), sensitive(true) { }

    void whitespace(const string& s) { white = s; }   // make s the whitespace set
    void add_white(char c) { white += c; } // add to the whitespace set
    bool is_whitespace(char c);       // is c in the whitespace set?

    void case_sensitive(bool b) { sensitive = b; }
    bool is_case_sensitive() { return sensitive; }

    Punct_stream& operator>>(string& s);
    operator bool();
```
