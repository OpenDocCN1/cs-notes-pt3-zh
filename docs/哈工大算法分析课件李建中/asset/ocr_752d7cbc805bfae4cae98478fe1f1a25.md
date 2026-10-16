# 7.2 Basic Tree Searching Strategies

+   - Breadth-First Search
+   - Depth-First Search

# Breadth-First Search

+   - 算法
+     1. 构造一个队列或队列Q;
+     2. If Q中有一个节点x且目标节点. Then 停止;
+     3. 从Q中取出x, 把x的所有子节点置入Q的末尾;
+     4. If Q空 Then 失败 Else goto 2.

# 例：求解8-Puzzle问题

# Depth-First Search

+   - 算法
+     1. 构造一个由栈构成的表或栈S;
+     2. If Top(S)是目标节点. Then 停止;
+     3. Pop(S), 把Top(S)所有子节点置入栈顶;
+     4. If S空 Then 失败 Else goto 2.

# 例1. 背包容量和问题
输入：S={7,5,1,2,10}
输出：是否存在S'⊆S, 使其Sum(S')≥9