# # 7.6 Shortest Path Problems

Example 1

What is the length of the shortest path between a and z in
the weighted graph shown in Figure 3?

Solution :Although the shortest path is easily found by
inspection,we will develop some ideas useful in understanding
Dijkstra’s algorithm. We will solve this problem by finding
the length of the shortest path from a to successive
vertices ,until z is reached.