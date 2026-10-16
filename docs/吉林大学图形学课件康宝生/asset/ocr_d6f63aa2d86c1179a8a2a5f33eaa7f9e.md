```
if(TestPt.x <= ClipBoundary[0].x) return TRUE;
if(ClipBoundary[1].y < ClipBoundary[0].y) // 裁剪边界为窗口左边界
    if(TestPt.x >= ClipBoundary[0].x) return TRUE;
    return FALSE;
}
void Output(Vertex newVertex, int *outLength, Vertex *OutVertexArray)
{
    (*outLength) ++;
    OutVertexArray[*outLength - 1].x = newVertex.x;
    OutVertexArray[*outLength - 1].y = newVertex.y;
}
```