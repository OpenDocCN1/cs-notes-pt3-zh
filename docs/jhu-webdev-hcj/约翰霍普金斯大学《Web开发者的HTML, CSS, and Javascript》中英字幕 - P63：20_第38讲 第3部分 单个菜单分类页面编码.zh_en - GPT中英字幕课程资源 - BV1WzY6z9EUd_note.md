# Web开发者的HTML, CSS, and Javascript：38：单个菜单分类页面编码（第三部分）

![](img/576d75de473058e86219d245d174d1f9_1.png)

## 概述
在本节课中，我们将继续完善单个菜单分类页面的编码工作。上一节我们完成了页面的HTML结构和CSS样式布局。本节中，我们将重点解决页面内容数据变化时可能出现的布局问题，并学习如何使用Bootstrap的网格系统工具来确保布局的稳定性。

---

![](img/576d75de473058e86219d245d174d1f9_1.png)

在本次讲座的第一和第二部分，我们已经创建了HTML和CSS样式，来布局我们的单个菜单分类页面。在本讲中，我们将通过使用之前部分创建的网格，来处理我们所显示数据的可变性。

在宣告本页面完成之前，让我们先在页面中添加大量菜单项。

以下是添加多个菜单项的示例代码。我们复制一个现有的菜单项区块，并创建多个副本。

```html
<!-- 菜单项 D01 -->
<div class="col-md-6">
  <div class="row">
    <div class="col-sm-5">
      <div class="menu-item-photo">
        <div>D01</div>
        <img class="img-responsive" width="250" height="150" src="images/menu/B/B-1.jpg" alt="Item">
      </div>
      <div class="menu-item-price">$10.95<span> (pint)</span> $14.95 <span>(quart)</span></div>
    </div>
    <div class="menu-item-description col-sm-7">
      <h3 class="menu-item-title">Veal with Mixed Vegetables</h3>
      <p class="menu-item-details">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Eaque inventore esse minima incidunt impedit. Asperiores, voluptatem. Sint aspernatur provident, rem odio dolorem eaque voluptatibus modi reprehenderit minima, itaque cupiditate totam.</p>
    </div>
  </div>
  <hr class="visible-xs">
</div>

<!-- 菜单项 D02 -->
<div class="col-md-6">
  <!-- ... 内容与D01类似，但ID和标题不同 ... -->
</div>

<!-- 菜单项 D03 -->
<div class="col-md-6">
  <!-- ... 内容 ... -->
</div>

<!-- 菜单项 D04 -->
<div class="col-md-6">
  <!-- ... 内容 ... -->
</div>

<!-- 菜单项 D05 -->
<div class="col-md-6">
  <!-- ... 内容 ... -->
</div>

<!-- 菜单项 D06 -->
<div class="col-md-6">
  <!-- ... 内容 ... -->
</div>
```

保存后，回到浏览器，可以看到它们排列得非常整齐。菜单项都很好地排列在此。如果挤压浏览器窗口，可以看到它们都能很好地对齐，并且在最小屏幕尺寸下也能很好地折叠。我们甚至可以看到之前设计的页脚。

接下来，我们需要测试一个在内容不受控制时非常重要的情况。换句话说，我们无法控制描述文本的长度。描述可能很短，也可能很长。我们不确定当描述文本的高度超过当前行或这个想象中的行时会发生什么。

让我们来看一下。例如，我们将第一个菜单项的描述文本变得长很多。

```html
<p class="menu-item-details">
  Lorem ipsum dolor sit amet, consectetur adipisicing elit. Eaque inventore esse minima incidunt impedit. Asperiores, voluptatem. Sint aspernatur provident, rem odio dolorem eaque voluptatibus modi reprehenderit minima, itaque cupiditate totam.
  <!-- 复制并粘贴上述段落多次以加长描述 -->
  Lorem ipsum dolor sit amet, consectetur adipisicing elit. Eaque inventore esse minima incidunt impedit. Asperiores, voluptatem. Sint aspernatur provident, rem odio dolorem eaque voluptatibus modi reprehenderit minima, itaque cupiditate totam.
  Lorem ipsum dolor sit amet, consectetur adipisicing elit. Eaque inventore esse minima incidunt impedit. Asperiores, voluptatem. Sint aspernatur provident, rem odio dolorem eaque voluptatibus modi reprehenderit minima, itaque cupiditate totam.
</p>
```

保存后，回到浏览器查看。可以看到第三个项目被推到了这边。它本应坐在这里。第四个项目本应仍在第二行。现在布局被打乱了。

那么，我们如何解决这个问题呢？有几种方法。

第一种方法是限制文本字段的长度。也就是说，可以规定只允许这么多字符，超出的部分将被截断。我们将根据我们的规格裁剪任何不适合这里的内容。这是一种相当严格的方法。并且很难向餐厅老板提出要求，说描述不能超过这个长度。尽管让描述简洁明了确实是个好主意，没人想读很长的描述。但同时，如果我们的布局现在反过来规定某个菜单项的描述能有多长，这听起来有点奇怪。

因此，我们可以做的是修复整个布局问题。

那么，为什么一开始会出现这个布局问题呢？请记住，Bootstrap中的网格布局（至少在当前版本中）是基于浮动元素的。所有这些元素都向左浮动。

当一个元素向左浮动，而它前面的某个元素变得太长时，会发生什么？它开始换行。现在它无法适应这一行，因为这个东西在这里凸出来了。所以它能适应的下一个位置就在这里。然后这个第四号元素试图向左浮动，但它不能，因为没有空间了。所以它去了下一行。

如果你回顾关于浮动的讲座，这是我们处理过的问题，还记得 `clear` 属性。这基本上就是我们需要在这里做的，只不过Bootstrap在其网格系统中预先内置了一个特殊的清除浮动工具来解决这些问题。

如果我们访问Bootstrap官网，现在我们在网格系统部分，可以看到这里提到了“响应式列重置”。这指的就是这个特定问题：当一列变得更大时，其余列会变得混乱。它告诉你，为了修复这个问题，需要在你的网格中添加另一个 `div`。这个 `div` 基本上有一个类 `clearfix`，然后有一个限定条件，说明这个 `div` 应该在何时显示。例如，他们希望只在屏幕为超小尺寸时显示为 `visible-xs-block`。

在我们的案例中，让我们看看。这个问题确实发生在大屏幕上，也发生在较小的屏幕上。在中型屏幕上似乎也发生了，但当我们到达这个部分时，由于我们已经堆叠了，这没有区别。所以在小屏幕上这不是问题，但在中型屏幕上肯定是问题，在大屏幕上绝对是问题。

我们可以通过在网格中放置这种类型的 `div` 来修复它。让我们回到代码编辑器。基本上，这是第一个，但我们需要在第二个之后。第二个是我们需要清除的。

所以，在第二个网格单元格之后，我们将放置一个清除浮动。但在我们的案例中，我们希望它在中型屏幕生效，并且也需要在大型屏幕生效时显示相同的东西。

以下是修复布局的代码示例。我们在每两个菜单项之后插入一个清除浮动的 `div`。

```html
<!-- 菜单项 D01 -->
<div class="col-md-6">...</div>

<!-- 菜单项 D02 -->
<div class="col-md-6">...</div>

<!-- 在第二个单元格后插入清除浮动，针对中型和大型屏幕 -->
<div class="clearfix visible-md-block visible-lg-block"></div>

<!-- 菜单项 D03 -->
<div class="col-md-6">...</div>

<!-- 菜单项 D04 -->
<div class="col-md-6">...</div>

<!-- 在第四个单元格后再次插入清除浮动 -->
<div class="clearfix visible-md-block visible-lg-block"></div>

<!-- 菜单项 D05 -->
<div class="col-md-6">...</div>

<!-- 菜单项 D06 -->
<div class="col-md-6">...</div>

<!-- 在第六个单元格后插入清除浮动 -->
<div class="clearfix visible-md-block visible-lg-block"></div>
```

保存后，回到浏览器查看我们的网站。可以看到这里清除得非常漂亮。当然，我们需要重复这个操作，在每个第二个单元格后插入这个 `div`。我们在这个之后插入了一个，现在需要在第四号之后和第六号之后插入。

让我们回到代码编辑器，实际执行这个操作。复制这个 `div`，在第三号之后（实际上我们需要在第四号之后插入）。这里是第四号，我们回到这里并在那里插入。现在，如果第三号和第四号的任何描述变得有点失控，我们的布局仍然会保持良好。

我们也需要在第六号之后放置这个。这里是第六号，向下滚动一点。我们要确保不要在这里犯错，在第六号之后，我们将那个 `div` 插入在那里。

回到浏览器，我们可以看到，布局仍然非常整齐。如果我们挤压窗口使其变为中等尺寸，它们仍然排列整齐。整个第二行被推下来，但仍然对齐得很好。可以看到三在四之前，没有以错误的方式浮动，其他一切看起来都很好。

## 总结
本节课中，我们一起学习了如何通过添加多个菜单项来测试页面布局的健壮性，并发现了当描述文本长度不一致时可能引发的浮动布局问题。我们深入探讨了Bootstrap网格系统基于浮动的原理，并学习了如何使用 `clearfix` 类和响应式可见性工具（`visible-md-block`、`visible-lg-block`）来强制清除浮动，从而确保每行两个菜单项的布局在任何内容长度下都能保持稳定。这完成了我们的单个分类页面，也基本上完成了整个网站的布局。剩下的工作就是动态地将内容插入到“菜单分类”下的每一个位置。目前我们只有“午餐”，并且只是重复插入一些随机图片。显然，我们希望所有这一切都能更动态地工作，但就布局而言，我们已经基本完成了。