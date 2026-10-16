```
/* 检验 */
bool test ( float b1_x, float b1_y,
    float b2_x, float b2_y,
    float b3_x, float b3_y) {
straightline(b1_x, b1_y, b2_x, b2_y);
if(fabs(b3_y-(a*b3_x+b))<eps)
    return true;
else
    return false;
}
```