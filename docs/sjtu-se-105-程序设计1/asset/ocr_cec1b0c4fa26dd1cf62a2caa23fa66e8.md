```
struct Text : Shape {
    Text(Point x, const string& s) // 点x是第一个字母的左下点位置
        : lab(s),
        fnt(fl_font()),     // 缺省的字体
        fnt_sz(fl_size())   // 缺省的字体大小
    { add(x); }             // 将 x 存储在Text继承的 Shape 部分中

    void draw_lines() const;

    // ... 常见的get 和set 成员函数 ...
private:
    string lab;     // 标签
    Font fnt;       // 标签的字体
    int fnt_sz;     // 字体大小
};
```