```
```cpp
OffBits = (LPBITMAPINFO)
// 找到DIB图像素起始
pDIBBits = pDoc->Iri...
// 获取当前DIB颜色数
if (iColorNum == 256)
{
    // 提示用户
    MessageBox("不是...
        MB_ICONINFOR...
    return;
}
// 更改光标形状
BeginWaitCursor();
// 计算DIB宽度
lWidth = pDoc->IrisImg...
// 计算DIB高度
lHeight = pDoc->IrisImg.Height();
// 计算图像像素总数
lCountSum = lHeight * lWidth;
// 分配内存
Red = new CHAR[lCountSum];
Green = new CHAR[lCountSum];
Blue = new CHAR[lCountSum];
// 计算图像每行的字节数
lLineBytes = (lWidth * 8 + 31) / 32;
// 重置计数为0
for (i = 0; i < lCountSum; i++)
{
```

```

+   - `Red`
+   - `Green`
+   - `Blue`

| Name | Value |
|---|---|
| Red | CXX0017: Error: symbol "Red" not found |
| Green | CXX0017: Error: symbol "Green" not found |
| Blue | CXX0017: Error: symbol "Blue" not found |