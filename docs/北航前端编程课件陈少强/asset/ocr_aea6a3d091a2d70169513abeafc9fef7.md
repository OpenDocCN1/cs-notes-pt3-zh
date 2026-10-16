# 2.7 CSS样式优先权

由于存在4种不同的样式使用方式，以及定义样式时的各种选择器，因此在CSS的样式定义中，难免存在重复定义。最终到底是哪个样式定义起作用？就是所谓的样式优先权问题。下面的原则与前页的“继承”是一致的：

+   - `!important`：加`!important`关键字的样式最优先。例如：
+     ```css
+     p{background-color:rgb(255,0,0) !important}
+     ```
+   - 局部优先：除`!important`外，内嵌样式表最优先。
+     ```html
+     <p style="background-color:#000">JavaScript</p>
+     ```
+   - 具体优先：选择器指定得越具体，样式越优先。
+     ```css
+     body{background-color:#ff0000}
+     body p{background-color:#00ff00}
+     ```
+   - 后者优先：同一元素同一样式的定义，后者优先。
+     ```css
+     p{background-color:#ff0000}
+     p{background-color:#00ff00}
+     ```