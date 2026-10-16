# 4.2.5 jQuery中用于遍历DOM的方法

2. 主要遍历方法

```
$('td:contains(Henry)').next().addClass('highlight'); //next()
$('td:contains(Henry)').nextAll().addClass('highlight'); //nextAll()
$('td:contains(Henry)').nextAll().andSelf().addClass('highlight'); //andSelf()
$('td:contains(Henry)').parent().children().addClass('highlight');//parent() 和children()
```

说明：连缀可以写在多行上以增加可读性。例如：

```
$('td:contains(Henry)') // Find every cell containing "Henry"
.parent() // Select its parent
.find('td:eq(1)') // Find the 2nd descendant cell
.addClass('highlight') // Add the "highlight" class
.end() // Return to the parent of the cell containing "Henry"
.find('td:eq(2)') // Find the 3rd descendant cell
.addClass('highlight'); // Add the "highlight" class
```