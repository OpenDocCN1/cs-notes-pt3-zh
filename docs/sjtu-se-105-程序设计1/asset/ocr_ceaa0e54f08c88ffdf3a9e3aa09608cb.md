+   - Shape 处理颜色和风格
+     - 它保持其数据的私有性，并提供访问函数
+       void set_color(Color col);
+       Color color() const;
+       void set_style(Line_style sty);
+       Line_style style() const;
+       // ...
+       private:
+       // ...
+       Color line_color;
+       Line_style ls;